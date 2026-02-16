# The @marianmeres ecosystem

> This document describes the "@marianmeres" ecosystem. Some packages are probably used in this project.

## Metadata

| | |
|---|---|
| **Language** | TypeScript |
| **Runtime** | Deno (primary), Node.js (via npm) |
| **Registry** | JSR (primary), npm (secondary) |
| **Local path** | `/Users/mm/projects/@marianmeres/{PACKAGE_NAME}/AGENTS.md` |

> Each package has an `AGENTS.md` file with detailed API documentation for AI agents.

## Reference

### Core Primitives

Building blocks for reactive state and messaging.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/store` | Reactive state (Svelte-compatible) | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/store/refs/heads/master/AGENTS.md) |
| `@marianmeres/pubsub` | Pub/sub event system | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/pubsub/refs/heads/master/AGENTS.md) |
| `@marianmeres/fsm` | FSM with `composeFsmConfig` | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/fsm/refs/heads/master/AGENTS.md) |
| `@marianmeres/actor` | Actor Model with `createTypedStateActor` | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/actor/refs/heads/master/AGENTS.md) |
| `@marianmeres/dtokit` | Typed message validation | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/dtokit/refs/heads/master/AGENTS.md) |
| `@marianmeres/clog` | Structured logger | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/clog/refs/heads/master/AGENTS.md) |
| `@marianmeres/ticker` | Store-compatible reactive timers | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/ticker/refs/heads/master/AGENTS.md) |
| `@marianmeres/batch` | Batch processor with flush triggers | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/batch/refs/heads/master/AGENTS.md) |

If the package at hand calls console.log|debug|error|warn at least once, then @marianmeres/clog is required.

Other commonly used packages are @marianmeres/store and @marianmeres/pubsub.

### State Management

Reactive state patterns and collections.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/modelize` | Proxy wrapper with dirty tracking | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/modelize/refs/heads/master/AGENTS.md) |
| `@marianmeres/wizard` | Multi-step wizard flow state | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/wizard/refs/heads/master/AGENTS.md) |
| `@marianmeres/item-collection` | Collection with active item tracking | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/item-collection/refs/heads/master/AGENTS.md) |
| `@marianmeres/ecsuite` | E-commerce state (cart, wishlist, orders) | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/ecsuite/refs/heads/master/AGENTS.md) |

### Web & Routing

HTTP servers, routing, middleware.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/demino` | Minimal Deno web framework | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/demino/refs/heads/master/AGENTS.md) |
| `@marianmeres/simple-router` | Framework-agnostic pattern router | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/simple-router/refs/heads/master/AGENTS.md) |
| `@marianmeres/midware` | Serial middleware framework | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/midware/refs/heads/master/AGENTS.md) |
| `@marianmeres/http-utils` | HTTP client with typed errors | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/http-utils/refs/heads/master/AGENTS.md) |
| `@marianmeres/signaling` | WebRTC signaling server (SSE) | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/signaling/refs/heads/master/AGENTS.md) |
| `@marianmeres/webrtc` | WebRTC connection management | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/webrtc/refs/heads/master/AGENTS.md) |

### Data & Persistence

Database, storage, SQL utilities.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/steve` | PostgreSQL job queue | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/steve/refs/heads/master/AGENTS.md) |
| `@marianmeres/kv` | Key-value storage abstraction | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/kv/refs/heads/master/AGENTS.md) |
| `@marianmeres/migrate` | Version migration framework | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/migrate/refs/heads/master/AGENTS.md) |
| `@marianmeres/condition-builder` | SQL WHERE clause builder | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/condition-builder/refs/heads/master/AGENTS.md) |
| `@marianmeres/condition-parser` | Search notation parser | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/condition-parser/refs/heads/master/AGENTS.md) |
| `@marianmeres/data-to-sql-params` | Objects to SQL parameters | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/data-to-sql-params/refs/heads/master/AGENTS.md) |

### Text & Search

String manipulation and search.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/searchable` | In-memory text search | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/searchable/refs/heads/master/AGENTS.md) |
| `@marianmeres/interpolate` | String interpolation (Docker-style) | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/interpolate/refs/heads/master/AGENTS.md) |

### UI Utilities

Frontend helpers and data structures.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/calendar-utils` | Calendar/date picker logic | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/calendar-utils/refs/heads/master/AGENTS.md) |
| `@marianmeres/tree` | Tree data structure | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/tree/refs/heads/master/AGENTS.md) |
| `@marianmeres/widget-provider` | Iframe widget embedding (float/fullscreen/inline) | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/widget-provider/refs/heads/master/AGENTS.md) |

### Auth & Security

Access control.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/rbac` | Role-Based Access Control | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/rbac/refs/heads/master/AGENTS.md) |

### Utilities

General-purpose helpers.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/topo-merge` | POJO inheritance via topo sort | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/topo-merge/refs/heads/master/AGENTS.md) |

### Build Tools

Development and release tooling.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/npmbuild` | Deno to npm package builder | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/npmbuild/refs/heads/master/AGENTS.md) |
| `@marianmeres/deno-build` | Bundle Deno TS for browser | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/deno-build/refs/heads/master/AGENTS.md) |
| `@marianmeres/deno-release` | Semantic version release CLI | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/deno-release/refs/heads/master/AGENTS.md) |

### Type Libraries

Type definitions.

| Package | Purpose | Docs |
|---------|---------|------|
| `@marianmeres/collection-types` | Ecosystem type definitions | [AGENTS.md](https://raw.githubusercontent.com/marianmeres/collection-types/refs/heads/master/AGENTS.md) |

## Instructions for implementation

If any task requires similar functionality covered by an @marianmeres package, it should be implemented preferably using that package.
