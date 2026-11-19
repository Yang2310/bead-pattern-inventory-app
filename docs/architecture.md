# Architecture and Engineering Decisions

[简体中文](architecture.zh-CN.md) | **English**

## System boundaries

The WeChat Mini Program owns user interaction and local UI state. A Python/FastAPI backend owns request validation, pattern/inventory business logic, and persistence. The client communicates through REST APIs; it does not query MySQL or object storage as a database.

    Mini Program UI
       | HTTPS / JSON REST
       v
    FastAPI routes / validation / services
       |----------------------|
       v                      v
    MySQL                  Tencent COS
    - pattern metadata     - persistent reference media
    - editable grid data   - uploaded image assets
    - progress/state
    - bead stock/logs

Selected text/image submission flows also use WeChat content-safety services. Environment configuration and operational credentials are not included in this public repository.

## Two pattern data paths

**Generated pattern:** original image -> processing/color matching -> structured bead grid -> editor/preview -> persisted grid/progress. The app can redraw and update the generated grid from structured data.

**Imported existing chart:** image upload -> crop/grid review and manual calibration when required -> chart view/progress -> stored cropped reference image and metadata. Imported charts are not presented as automatic recognition of every bead code.

These routes share downstream pattern management and inventory concepts, but not identical media/storage needs.

## Inventory transaction design

Pattern actions can change inventory only according to backend business rules. The project records stock changes with references to pattern-related operations. Important scenarios include incremental synchronization of completed regions, completion, restart, and deletion, with safeguards against duplicate application of the same stock change. These are design and implementation facts; not a claim that all race conditions are formally proven absent.

## Query optimization from a real failure

Large structured pattern JSON was previously loaded during list queries and caused a MySQL sort-memory error. The implementation defers this large field for list retrieval so the listing path fetches lightweight pattern metadata instead. The full structured data remains available for detail/edit views when needed.

## Deployment boundary

The repository documents Docker Compose + Nginx self-hosted deployment and backend health/readiness endpoints. The full source and configuration remain private. A prior deployment existed, but no permanently hosted public demo is promised.

## Further reading

- [Feature walkthrough](features.md)
- [Portfolio status](project-status.md)
- [Demo and screenshot upload instructions](../assets/README.md)
