# Product Features

## 1. Home & Navigation

The Mini Program provides a dedicated home experience that routes users into pattern creation, saved patterns, and inventory workflows.

## 2. Generate a Pattern from an Image

Users can select an image and move through an image-to-pattern workflow. The processed result becomes structured application data that can be previewed, edited, and saved.

**Demonstrates:** image processing, frontend/backend coordination, structured JSON data, persistence.

## 3. Upload an Existing Pattern

The application also supports users who already have a bead-pattern image and want to manage it inside the app rather than generate a new one.

**Demonstrates:** multiple input workflows sharing the same downstream product model.

## 4. Pattern Library

Saved patterns are presented as a reusable library. Users can reopen patterns and continue interacting with them instead of treating generation as a one-time action.

**Demonstrates:** persistent application state and CRUD workflows.

## 5. Pattern Progress

Pattern state can be saved so users can track ongoing work. This connects the visual pattern experience with persisted backend data.

**Demonstrates:** state synchronization between client and backend.

## 6. Inventory by Series and Color

Users can manage bead stock at different levels, including broader series views and individual color quantities.

**Demonstrates:** relational data modeling and practical inventory UI.

## 7. Inventory Transactions

Inventory changes are tied to pattern lifecycle events. The backend records enough state to avoid incorrect repeated deductions or restorations when users complete, restart, or delete patterns.

**Demonstrates:** server-side business rules beyond basic CRUD.

## 8. Cloud Media Storage

Persistent image assets are stored in Tencent COS instead of depending on temporary application-container storage.

**Demonstrates:** object-storage integration and separation of structured data from media assets.

## 9. Content Safety

Selected text and image inputs can be checked through WeChat content-safety services before being accepted into user-facing workflows.

**Demonstrates:** third-party API integration and moderation-aware product design.

## 10. Deployment & Service Health

The backend supports containerized self-hosted deployment with Nginx and exposes health/readiness endpoints for operational verification.

**Demonstrates:** Docker-based deployment, reverse proxy configuration, environment-based configuration, and basic service observability.

---

Screenshots will be added alongside these sections as the public portfolio repository is expanded.