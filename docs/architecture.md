# Architecture

## Overview

The application is split into a WeChat Mini Program client and a Python/FastAPI backend. Structured business data and long-lived media are stored separately so each storage layer serves a clear purpose.

```text
WeChat Mini Program
        │
        │ HTTPS / JSON REST API
        ▼
     FastAPI
        │
        ├── authentication / user context
        ├── pattern workflows
        ├── inventory workflows
        ├── image-processing workflows
        ├── content-safety integration
        └── health / readiness endpoints
        │
        ├──────────────► MySQL
        │                patterns, inventory,
        │                transactions, metadata
        │
        └──────────────► Tencent COS
                         persistent image assets
```

## Client Layer

The WeChat Mini Program provides the product interface. It contains separate workflows for the home screen, inventory, pattern library, pattern upload, pattern generation preview, editing, and supporting pages.

The client communicates with the backend through JSON REST requests rather than accessing the database directly.

## API Layer

FastAPI provides the boundary between the Mini Program and application services. The backend is responsible for validating requests, applying business rules, coordinating persistence, and returning structured responses to the client.

This keeps important rules—such as inventory adjustments—on the server instead of relying only on frontend state.

## Pattern Processing

Pattern creation begins with an image workflow. Image-processing output is converted into structured pattern data that can be persisted and edited later. This allows the application to work with bead colors and quantities as data rather than treating the pattern as only an exported picture.

## Inventory Consistency

Inventory is connected to pattern lifecycle actions. Completion can consume inventory, while restart or deletion can restore previously consumed quantities according to the stored transaction state.

This part of the application required explicit business rules because a simple CRUD implementation would allow repeated actions to produce incorrect stock counts.

## Storage Strategy

### MySQL

Used for structured application data such as pattern metadata, bead inventory, series information, progress, and transaction-related state.

### Tencent COS

Used for persistent media assets. This separates binary/object storage from relational application data and avoids relying on temporary local container storage.

## External APIs

WeChat content-safety APIs are integrated for selected user-submitted text and image flows.

## Deployment

The backend supports a self-hosted deployment path based on Docker Compose and Nginx. Environment-specific settings are provided through configuration rather than being hard-coded into application logic.

The service exposes health/readiness checks so deployment status can be verified independently of the Mini Program UI.

## Showcase Note

This document describes the architecture at a portfolio level. Production source code, credentials, infrastructure secrets, and private operational details are intentionally excluded.