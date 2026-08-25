# Bead Pattern & Inventory App

A full-stack WeChat Mini Program for creating, managing, and tracking pixel-bead patterns and bead inventory.

> **Role:** Independent full-stack developer  
> **Focus:** FastAPI backend · REST APIs · image-to-pattern workflow · inventory management · cloud storage · deployment

**English** | [简体中文](README.zh-CN.md)

## Project Overview

This project was built as a practical end-to-end application rather than a standalone demo. It combines a WeChat Mini Program frontend with a FastAPI backend to support the complete workflow around pixel-bead pattern creation and inventory management.

Users can convert ordinary images into structured bead patterns, upload existing pattern images, manage bead stock, track inventory changes, save pattern progress, and keep persistent assets in cloud object storage.

The private source repository contains the full implementation. This public repository is a portfolio showcase focused on product capabilities, architecture, and engineering decisions.

## What I Built

- A WeChat Mini Program frontend with multiple user workflows
- A Python / FastAPI backend exposing REST APIs for application data and business logic
- Image-to-pattern conversion and pattern preview workflows
- Editable pattern data with saved progress
- Bead inventory management at both series and individual color levels
- Inventory transaction tracking when patterns are completed, restarted, or deleted
- Persistent image storage with Tencent COS
- Structured business data stored in a relational database
- WeChat content-safety checks for user-submitted names and images
- Docker- and Nginx-based self-hosted deployment support
- Health and readiness checks for backend deployment

## Product Workflow

```text
User image / existing pattern
          ↓
   WeChat Mini Program
          ↓
      FastAPI REST API
          ↓
Image processing + business rules
          ↓
Structured pattern / inventory data
          ↓
 MySQL database + Tencent COS
```

The application supports both pattern creation and day-to-day inventory management, so generated patterns are connected to actual bead usage rather than being isolated image-processing outputs.

## Key Capabilities

### Image-to-Pattern Conversion

Users can upload an image and convert it into a structured bead pattern for editing and preview. The generated result is stored as application data rather than only as a flat image, which allows the app to track bead colors, quantities, editing state, and progress.

### Pattern Management

The app supports generated patterns as well as uploaded existing patterns. Users can manage saved patterns, preview them, record progress, restart a pattern, and delete it according to application business rules.

### Inventory Management

Inventory can be managed by bead series or individual bead color. Stock changes are recorded through transaction logic so pattern completion, restart, and deletion can update or restore inventory consistently.

### Backend & Storage

FastAPI handles API routing, data validation, persistence, and application workflows. Long-lived images are stored in Tencent COS, while structured pattern and inventory data are stored in the database.

### Safety & User Data

User-submitted text and images can be checked through WeChat content-safety APIs. The application also includes feedback, privacy information, and user-data cleanup flows.

## Architecture

```text
┌────────────────────────────┐
│   WeChat Mini Program UI   │
└──────────────┬─────────────┘
               │ HTTPS / REST
               ▼
┌────────────────────────────┐
│       FastAPI Backend      │
│ API · validation · logic   │
└──────────┬───────────┬─────┘
           │           │
           ▼           ▼
┌────────────────┐  ┌─────────────────┐
│ MySQL Database │  │   Tencent COS   │
│ structured data│  │ persistent media│
└────────────────┘  └─────────────────┘
           │
           ▼
┌────────────────────────────┐
│ WeChat Content Safety API  │
└────────────────────────────┘
```

More detail: [docs/architecture.md](docs/architecture.md)

## Tech Stack

**Frontend**
- WeChat Mini Program
- JavaScript / WXML / WXSS

**Backend**
- Python
- FastAPI
- REST API

**Data & Storage**
- MySQL
- Tencent COS

**Deployment**
- Docker
- Docker Compose
- Nginx
- HTTPS

**External Integration**
- WeChat content-safety API

## Engineering Highlights

This project demonstrates more than interface implementation. It required coordinating UI state, API design, relational data, file storage, image-processing workflows, inventory consistency, external APIs, and deployment.

The backend supports environment-based configuration and health/readiness endpoints, while the project structure separates application code, deployment resources, maintenance scripts, and tests.

## Screenshots

Product screenshots will be added here as the public showcase is expanded.

Planned showcase views include:

- Home and main navigation
- Image upload and pattern generation
- Pattern preview / editing
- Pattern library
- Inventory management
- Inventory editing and series views

## What This Project Demonstrates

- Building a complete product workflow from frontend to backend
- Designing and implementing FastAPI REST APIs
- Managing relational application data and business rules
- Integrating object storage and third-party APIs
- Connecting image-processing output to structured application state
- Handling inventory consistency across multiple user actions
- Preparing a Python backend for containerized self-hosted deployment
- Organizing a multi-part application for maintainability and testing

## Public Showcase Scope

This repository intentionally does **not** contain the private production source code, credentials, user data, database contents, or deployment secrets.

It is maintained as a portfolio repository to document the product, architecture, technical decisions, and selected non-sensitive screenshots.