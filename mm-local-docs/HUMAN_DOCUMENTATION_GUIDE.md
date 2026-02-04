# Human Documentation Guide

> **Purpose**: Instructions for maintaining human-facing documentation (README.md and API.md).

---

## 1. Core Principles

| Principle | Description |
|-----------|-------------|
| **Conservative updates** | Only modify if inaccurate or clearly improvable |
| **Separation of concerns** | README = concise overview; API.md = comprehensive reference |
| **Link, don't duplicate** | README references API.md for full details |
| **Read before writing** | Always check existing content first |

---

## 2. README.md

### 2.1 Required Badges

Place immediately below the main title (`# Package Name`):

```markdown
[![NPM](https://img.shields.io/npm/v/PACKAGE)](https://www.npmjs.com/package/PACKAGE)
[![JSR](https://jsr.io/badges/@SCOPE/PACKAGE)](https://jsr.io/@SCOPE/PACKAGE)
[![License](https://img.shields.io/npm/l/PACKAGE)](LICENSE)
```

Replace `PACKAGE` and `@SCOPE/PACKAGE` with actual values.

### 2.2 Required Sections

| Section | Content |
|---------|---------|
| **Description** | 1-2 sentences explaining what the package does |
| **Installation** | npm and/or jsr install commands |
| **Usage** | Concise example(s) demonstrating primary use case |
| **API Reference** | Link to API.md (not full API embedded) |
| **License** | License type with link |

### 2.3 Template

```markdown
# Package Name

[![NPM](https://img.shields.io/npm/v/PACKAGE)](https://www.npmjs.com/package/PACKAGE)
[![JSR](https://jsr.io/badges/@SCOPE/PACKAGE)](https://jsr.io/@SCOPE/PACKAGE)
[![License](https://img.shields.io/npm/l/PACKAGE)](LICENSE)

[One-line description of what the package does.]

## Installation

```bash
npm install PACKAGE
```

## Usage

```typescript
import { ... } from 'PACKAGE';

// Minimal working example
```

## API

See [API.md](API.md) for complete API documentation.

## License

[MIT](LICENSE)
```

### 2.4 Update Rules

- If README already contains embedded API documentation, extract full details to API.md and keep only essential usage examples in README
- Preserve any additional sections the author included (e.g., Contributing, Changelog references)
- Do not remove content unless it's clearly outdated or incorrect

---

## 3. API.md

### 3.1 Purpose

Full public API documentation in human-friendly format. This is not a JSDoc dump — write for humans who want to understand and use the API.

### 3.2 Structure

Organize by export type:

```markdown
# API

## Functions

### `functionName(param1, param2)`

Description of what the function does.

**Parameters:**
- `param1` (Type) — Description
- `param2` (Type, optional) — Description. Default: `value`

**Returns:** `ReturnType` — Description

**Example:**
```typescript
const result = functionName('value', { option: true });
```

---

## Types

### `TypeName`

```typescript
type TypeName = {
  property: string;
  optional?: number;
};
```

Description if needed.
```

### 3.3 Guidelines

- Include all public exports
- Provide at least one example per function/class
- Document parameters with types and defaults
- Keep descriptions concise but complete
- Group related items logically

### 3.4 Template

```markdown
# API

## Functions

### `mainFunction(options)`

[Description]

**Parameters:**
- `options` (Object)
  - `options.property` (Type) — Description

**Returns:** `ReturnType`

**Example:**
```typescript
// Example code
```

---

## Types

### `MainType`

```typescript
// Type definition
```

---

## Constants

### `CONSTANT_NAME`

`value` — Description
```

---

## 4. Update Workflow

```
1. READ existing README.md and API.md
2. COMPARE with current codebase (exports, signatures, behavior)
3. DECIDE: Is update needed?
   - If accurate and complete → do not modify
   - If inaccurate or improvable → update
4. UPDATE following templates above
5. VERIFY all examples work
```

---

## 5. When to Create vs Update

| Scenario | Action |
|----------|--------|
| Files don't exist | Create both using templates |
| README has embedded full API | Extract to API.md, simplify README |
| API.md missing exports | Add missing entries |
| Examples outdated | Update examples only |
| Files accurate | Do nothing |

---

## Invocation

```
Update README and API docs.
Reference: HUMAN_DOCUMENTATION_GUIDE.md
```
