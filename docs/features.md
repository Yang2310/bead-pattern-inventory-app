# Product Features

[简体中文](features.zh-CN.md) | **English**

## 1. Home and navigation
Entry points for pattern generation, importing existing patterns, the saved pattern library, and bead inventory. **Shows:** practical multi-page Mini Program UI.

## 2. Generate an editable bead pattern
Convert an ordinary image into bead-grid data with color matching, preview, cell editing, and saved results. The generated pattern is structured data, not just a flat exported image. **Shows:** image processing, APIs, data modeling.

## 3. Import an existing chart
Upload and crop an existing chart, review or manually calibrate the grid, and keep a reference image for continued work. **Important:** fully automatic bead-code recognition is not claimed. **Shows:** a separate import workflow with explicit user correction.

## 4. Pattern library and progress
Browse saved generated/imported patterns, reopen them, manage pattern state, mark areas complete, and retain progress. **Shows:** persisted state and multi-step product flows.

## 5. Inventory by series and color
View, search, and adjust bead stock by palette/series and individual color. **Shows:** relational records and inventory operations.

## 6. Inventory settlement and history
Log stock changes caused by direct adjustments and relevant pattern lifecycle operations. Repeated synchronization and restarts need careful accounting to avoid double deduction. **Shows:** nontrivial backend business rules and transaction traceability.

## 7. Media and business-data storage
Keep structured pattern/inventory state in MySQL and persistent image assets in Tencent COS as appropriate to the workflow. **Shows:** separation of database and object storage responsibilities.

## 8. Content safety and user flows
Selected user-submitted names/images are checked through WeChat content-safety services; product flows also include feedback, privacy information, and data cleanup. **Shows:** third-party API integration.

## 9. Deployment and performance
Docker Compose/Nginx setup, health/readiness checks, and deferred loading of large pattern JSON for list queries. **Shows:** deployment preparation and debugging of a concrete MySQL memory problem.

## Visual walkthrough

**[Watch the real 3:18 Mini Program demo](../assets/demo/PinDou_English_Portfolio_Demo.mp4)**, or open the [media guide](../assets/README.md) for the video chapters and English captions. Standalone screenshots remain optional.

[Back to English README](../README.md)
