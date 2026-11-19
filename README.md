# Bead Pattern & Inventory App

**Full-stack WeChat Mini Program | Python · FastAPI · MySQL · image processing · Tencent COS**

A practical app for turning images into editable pixel-bead patterns, tracking making progress, and managing bead inventory in one workflow.

**Role:** Independent full-stack developer, with AI-assisted implementation and hands-on integration, testing, and debugging.  
**Project status:** Core product implemented and previously deployed; no continuously available public live demo.  
**Source:** Private implementation; this repository is its public, non-sensitive portfolio showcase.

**English** | [简体中文](README.zh-CN.md)

## Watch the product

**Demo video: coming soon.** A real Mini Program walkthrough will be linked here after recording; there is no placeholder video pretending to be a demo.

**Screenshots: coming soon.** Planned views: home, image-to-pattern conversion, pattern editing/progress, inventory, and inventory history.

The reserved upload folders are [assets/screenshots](assets/screenshots/) and [assets/demo](assets/demo/). See the bilingual [media upload guide](assets/README.md). No WeChat installation or source-code access will be required to watch the eventual video.

## What the product does

1. **Create a pattern from an image.** Convert an ordinary image to structured bead-grid data, preview and edit bead colors, and save the resulting pattern and progress.
2. **Import an existing chart.** Upload a bead-chart image, crop/calibrate its grid as needed, and manage it in the same pattern library. This workflow includes manual calibration; it is **not** described as fully automatic recognition.
3. **Work on a pattern.** Reopen saved projects, inspect bead requirements, mark completed sections, and track progress.
4. **Manage bead stock.** View inventory by palette/series and bead color, edit quantities, and inspect stock-change history.
5. **Connect patterns to inventory.** Pattern progress/completion and restart/deletion use backend rules and transaction records for stock consumption or restoration.

Detailed workflow descriptions: [Product features](docs/features.md).

## Engineering highlights

- **Full-stack API architecture:** WeChat Mini Program UI communicates with a Python/FastAPI backend through REST APIs. Business rules and persistence are handled on the server.
- **Structured image processing:** generated patterns store editable grid/color and progress data, rather than relying solely on a flattened image; imported charts can retain their cropped reference images.
- **Inventory consistency:** stock changes are linked to pattern lifecycle events and transaction logs; the design must avoid duplicate deductions when a completed region is synced repeatedly.
- **A real database performance fix:** the pattern-list query was adjusted to defer loading a large structured JSON field, avoiding a MySQL sort-memory failure during list retrieval.
- **External services and deployment:** MySQL for structured records, Tencent COS for persistent media, WeChat content-safety integrations, and Docker/Nginx configuration with health/readiness endpoints.

The engineering decisions above describe the implemented project and the documented integration work. They do not imply that every edge case has been independently certified, or that a live production environment is available today.

## Architecture at a glance

    WeChat Mini Program (JavaScript / WXML / WXSS)
                       |
                  HTTPS / REST
                       |
                FastAPI backend
          authentication / API validation
          pattern processing / inventory rules
                  /          \
               MySQL       Tencent COS
        patterns, stock,    persistent media
         progress, logs
                       |
             WeChat content-safety API
               (selected inputs)

See [Architecture and design decisions](docs/architecture.md).

## Technology

| Area | Stack |
| --- | --- |
| Frontend | WeChat Mini Program, JavaScript, WXML, WXSS |
| Backend | Python, FastAPI, REST APIs |
| Image/data | Pillow-style image processing, structured pattern data |
| Persistence | MySQL, Tencent COS |
| Operations | Docker, Docker Compose, Nginx, HTTPS, service health checks |
| External API | WeChat content-safety services |

## What is publicly verifiable?

- Product workflows and engineering decisions: [features](docs/features.md) and [architecture](docs/architecture.md)
- Project availability and limitations: [status](docs/project-status.md)
- Recorded UI evidence: **pending upload** (see [media guide](assets/README.md))
- Full implementation and private operational data: **not published**

This showcase intentionally excludes production source code, user records, database dumps, credentials, cloud configuration secrets, and private training assets. It is not a runnable copy of the private application.

---

[中文版 README](README.zh-CN.md) · [Media upload guide / 素材上传说明](assets/README.md)
