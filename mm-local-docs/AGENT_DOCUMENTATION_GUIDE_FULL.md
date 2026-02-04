# Agent Documentation Creation Guide

> **Purpose**: This document provides instructions for creating comprehensive, token-efficient documentation that enables AI coding agents to effectively understand and work within a codebase.

---

## 1. Core Principles

### 1.1 Design Philosophy

Agent documentation differs fundamentally from human documentation. Optimise for these characteristics:

| Principle | Description |
|-----------|-------------|
| **Declarative over narrative** | State facts directly; avoid explanatory prose |
| **Scannable over readable** | Use consistent structure, headers, and lists |
| **Modular over monolithic** | Separate concerns into linkable documents |
| **Actionable over descriptive** | Focus on what to do, not backstory |
| **Explicit over implicit** | Never assume prior context or conventions |

### 1.2 Token Efficiency Guidelines

- Keep the root entry document under 1,500 tokens (~1,000 words)
- Domain-specific documents should be 500–2,000 tokens each
- Prefer inline code examples over lengthy explanations
- Use tables for structured information (more compact than lists)
- Avoid redundancy across documents; use cross-references instead
- Front-load critical information; place details at the end

### 1.3 Information Hierarchy

Structure all documentation in layers of increasing specificity:

```
Level 0: Entry Point (always consumed)
    └── Level 1: Architecture & Conventions (consumed on first interaction)
            └── Level 2: Domain Documentation (consumed when relevant)
                    └── Level 3: Inline Documentation (consumed with code)
```

---

## 2. Documentation Structure

### 2.1 Required Files

Create the following documentation structure at minimum:

```
/project-root
│
├── AGENTS.md                    # Entry point (Level 0)
│
├── /docs
│   ├── architecture.md          # System design (Level 1)
│   ├── conventions.md           # Code standards (Level 1)
│   ├── tasks.md                 # Common task procedures (Level 1)
│   │
│   └── /domains                 # Domain-specific docs (Level 2)
│       ├── [domain-name].md
│       └── ...
│
└── [Per-module README.md]       # Inline documentation (Level 3)
```

### 2.2 File Naming Conventions

- Use lowercase with hyphens for multi-word names: `user-authentication.md`
- Domain docs should match directory or module names where possible
- Keep names concise but descriptive

---

## 3. Document Specifications

### 3.1 Entry Point Document (AGENTS.md)

**Location**: Project root  
**Token budget**: 800–1,500 tokens  
**Purpose**: Orient the agent; provide essential facts; direct to deeper resources

**Required sections**:

```markdown
# [Project Name] — Agent Guide

## Quick Reference
- **Stack**: [Primary technologies]
- **Language**: [Language and version]
- **Package manager**: [npm/yarn/pnpm/etc.]
- **Run**: `[dev command]`
- **Test**: `[test command]`
- **Build**: `[build command]`

## Project Structure
[Brief directory overview with purpose of each top-level folder]

## Critical Conventions
[5–10 most important rules that apply project-wide]

## Before Making Changes
[Checklist of things to verify before modifying code]

## Documentation Index
[Links to architecture, conventions, domain docs with brief descriptions of when to consult each]
```

**Guidelines**:
- This file should be self-sufficient for simple tasks
- Include only information that applies globally
- Every statement should be actionable or directly useful

---

### 3.2 Architecture Document (architecture.md)

**Location**: `/docs/architecture.md`  
**Token budget**: 1,000–2,500 tokens  
**Purpose**: Explain system structure, data flow, and component relationships

**Required sections**:

```markdown
# Architecture

## System Overview
[One paragraph describing what the system does]

## Component Map
[Diagram or structured list of major components and their responsibilities]

## Data Flow
[How data moves through the system for primary use cases]

## External Dependencies
[Third-party services, APIs, databases with connection details]

## Key Files
[Map of important files/modules and their roles]

## Security Boundaries
[Authentication, authorisation, data isolation patterns]
```

**Guidelines**:
- Use ASCII diagrams or structured lists; avoid relying on images
- Focus on relationships and boundaries, not implementation details
- Include file paths to help agents locate components

---

### 3.3 Conventions Document (conventions.md)

**Location**: `/docs/conventions.md`  
**Token budget**: 500–1,500 tokens  
**Purpose**: Define code style, patterns, and standards

**Required sections**:

```markdown
# Code Conventions

## File Organisation
[How files should be named, organised, and structured]

## Naming Conventions
[Variables, functions, classes, files, database entities]

## Patterns
[Standard patterns used in the codebase with examples]

## Anti-Patterns
[What to avoid, with reasoning]

## Error Handling
[How errors should be created, propagated, and handled]

## Testing Standards
[Test file location, naming, coverage expectations]
```

**Guidelines**:
- Provide concrete examples for each convention
- Use "Do / Don't" comparisons for clarity
- Keep examples minimal but complete

**Example format**:

```markdown
## Error Handling

Pattern: Return result objects; do not throw exceptions in services.

✅ Do:
```js
function getUser(id) {
  const user = db.find(id);
  if (!user) return { data: null, error: 'USER_NOT_FOUND' };
  return { data: user, error: null };
}
```

❌ Don't:
```js
function getUser(id) {
  const user = db.find(id);
  if (!user) throw new Error('User not found');
  return user;
}
```
```

---

### 3.4 Tasks Document (tasks.md)

**Location**: `/docs/tasks.md`  
**Token budget**: 1,000–3,000 tokens  
**Purpose**: Provide step-by-step procedures for common development tasks

**Structure**:

```markdown
# Common Tasks

## Adding a New [Entity/Feature/Endpoint]

### Steps
1. [Step with specific file paths]
2. [Step with code pattern to follow]
3. [Step for testing/validation]

### Template
[Minimal code template if applicable]

### Checklist
- [ ] [Verification item]
- [ ] [Verification item]

---

## [Next task type]
...
```

**Guidelines**:
- Focus on the 5–10 most frequent development tasks
- Include exact file paths and commands
- Provide minimal working templates
- Add verification checklists

---

### 3.5 Domain Documents (/docs/domains/[name].md)

**Location**: `/docs/domains/`  
**Token budget**: 500–2,000 tokens per domain  
**Purpose**: Deep context for specific subsystems or feature areas

**Required sections**:

```markdown
# [Domain Name]

## Overview
[One-paragraph description of this domain's responsibility]

## Key Files
| File | Purpose |
|------|---------|
| `path/to/file.js` | [Brief description] |

## Data Model
[Entities, schemas, or types relevant to this domain]

## Business Rules
[Domain-specific logic that must be preserved]

## Integration Points
[How this domain interacts with other domains or external services]

## Common Operations
[Brief procedures for typical tasks within this domain]
```

**Guidelines**:
- Create one document per bounded context or major feature area
- Include business rules that aren't obvious from code
- Reference related domains rather than duplicating content

---

### 3.6 Inline Documentation (Module-Level)

**Location**: Within source code directories  
**Format**: Header comments or local README.md  
**Purpose**: Provide context that should be read with the code

**When to use module README.md**:
- Complex modules with non-obvious architecture
- Modules with critical invariants or constraints
- Shared libraries used across the codebase

**Header comment template**:

```javascript
/**
 * [Module Name]
 * 
 * Purpose: [One-line description]
 * 
 * Key concepts:
 * - [Concept]: [Brief explanation]
 * - [Concept]: [Brief explanation]
 * 
 * Invariants:
 * - [Rule that must always be true]
 * 
 * Usage:
 * ```
 * [Minimal example]
 * ```
 * 
 * See also: [link to relevant domain doc]
 */
```

---

## 4. Writing Guidelines

### 4.1 Language and Tone

- Use imperative mood: "Create the file" not "You should create the file"
- Be direct: "This module handles X" not "This module is responsible for handling X"
- Avoid hedging: "Use X" not "Consider using X" (unless options are genuinely equivalent)
- Omit unnecessary words: "Returns user object" not "This function returns the user object"

### 4.2 Code Examples

- Keep examples minimal: show only what's necessary to illustrate the point
- Use realistic names: `getUserById` not `foo` or `myFunction`
- Include imports only when they clarify usage
- Add brief comments only for non-obvious lines

### 4.3 Formatting Standards

**Use tables for structured data**:

```markdown
| Pattern | When to Use | Example |
|---------|-------------|---------|
| Service | Business logic | `UserService` |
| Repository | Data access | `UserRepository` |
```

**Use code blocks with language hints**:

````markdown
```typescript
const result: Result<User> = await getUser(id);
```
````

**Use blockquotes for warnings or important notes**:

```markdown
> ⚠️ **Warning**: Never store passwords in plain text.
```

### 4.4 Cross-Referencing

- Use relative paths: `See [conventions](./conventions.md)`
- Reference specific sections: `See [Error Handling](./conventions.md#error-handling)`
- Keep references unidirectional where possible to reduce coupling

---

## 5. Iterative Updates

This guide supports both initial documentation creation and incremental updates. When running against a project that already has agent documentation, follow this process.

### 5.1 Pre-Update Analysis

Before modifying any documentation, perform this assessment:

```markdown
## Documentation Audit

### Existing Documentation Found
- [ ] AGENTS.md (Entry point)
- [ ] docs/architecture.md
- [ ] docs/conventions.md
- [ ] docs/tasks.md
- [ ] docs/domains/*.md (list each)
- [ ] Inline module documentation

### Current State Assessment
For each existing document:
1. Last modified date (if available)
2. Sections present
3. Sections missing per this guide's specifications
4. Outdated content (references to files/patterns that no longer exist)

### Codebase Changes Since Last Update
1. New directories or modules added
2. New domains or feature areas
3. Changed patterns or conventions
4. Removed or relocated files
5. New external dependencies
```

### 5.2 Update Modes

Operate in one of these modes based on context:

| Mode | Trigger | Behaviour |
|------|---------|-----------|
| **Create** | No existing agent docs | Generate full documentation structure |
| **Extend** | Docs exist but lack coverage | Add missing sections and domains; preserve existing content |
| **Refresh** | Docs exist but are outdated | Update stale references; preserve accurate content |
| **Restructure** | Docs exist but don't follow this guide | Migrate content to recommended structure |

### 5.3 Incremental Update Rules

**Rule 1: Preserve accurate existing content**

Never delete or overwrite documentation that is still accurate. If unsure whether content is current, flag it for human review rather than removing it.

**Rule 2: Identify deltas explicitly**

When adding content, clearly distinguish new material:

```markdown
## Domains Index

- [Authentication](./docs/domains/auth.md) — User auth and sessions
- [Billing](./docs/domains/billing.md) — Payment processing
- [Notifications](./docs/domains/notifications.md) — *(Added: covers new email/push system)*
```

The "Added" annotation can be removed in subsequent cleanup but helps during review.

**Rule 3: Update, don't duplicate**

If information already exists in a different location or format:
- Consolidate into the canonical location per this guide
- Remove the duplicate
- Add a cross-reference if the old location might still be accessed

**Rule 4: Maintain cross-reference integrity**

When adding new domain documents:
1. Add entry to AGENTS.md documentation index
2. Add cross-references from related domain docs
3. Update architecture.md if new component relationships exist

### 5.4 Update Procedure

Follow this sequence for incremental updates:

```
1. AUDIT
   └── Scan existing documentation structure
   └── Scan codebase for undocumented areas
   └── Identify gaps and outdated content

2. PLAN
   └── List specific changes needed
   └── Determine update mode (extend/refresh/restructure)
   └── Prioritise by impact

3. UPDATE (in order)
   └── Domain documents (new or modified domains first)
   └── Tasks document (new procedures)
   └── Conventions document (new patterns)
   └── Architecture document (structural changes)
   └── Entry point (update index, quick reference)

4. VALIDATE
   └── Verify all file paths
   └── Check cross-references
   └── Confirm token budgets
   └── Run simulated agent test
```

### 5.5 Change Detection Heuristics

To identify what needs documentation updates, examine:

| Signal | Indicates |
|--------|-----------|
| New top-level directories | Potential new domain |
| New files in existing domains | Extended functionality to document |
| Modified package.json / dependencies | New external integrations |
| New database migrations | Schema changes for data model docs |
| Deleted files referenced in docs | Outdated documentation |
| New patterns appearing in 3+ files | Convention to document |

### 5.6 Reporting Updates

After completing incremental updates, generate a summary:

```markdown
## Documentation Update Summary

**Date**: [Date]
**Mode**: [Create/Extend/Refresh/Restructure]

### Added
- docs/domains/notifications.md (new domain)
- Tasks: "Adding push notifications" procedure

### Modified  
- AGENTS.md: Updated project structure, added notifications to index
- architecture.md: Added notification service to component map

### Flagged for Review
- docs/domains/billing.md: References to Stripe v2 API may be outdated

### Verified Current
- docs/conventions.md: All patterns still in use
- docs/domains/auth.md: No changes needed
```

---

## 6. Maintenance

### 6.1 Update Triggers

Documentation must be updated when:

- New patterns or conventions are introduced
- Directory structure changes significantly
- New domains or major features are added
- Existing documented behaviour changes
- Common agent errors indicate missing context

### 6.2 Review Checklist

Periodically verify:

- [ ] Entry point reflects current project state
- [ ] All file paths in docs are valid
- [ ] Code examples match current conventions
- [ ] No contradictions between documents
- [ ] Token budgets are respected
- [ ] Cross-references are not broken

### 6.3 Version Alignment

Consider adding a version or last-updated timestamp to each document:

```markdown
---
last_updated: 2025-01-15
applies_to: v2.x
---
```

---

## 7. Anti-Patterns to Avoid

| Anti-Pattern | Problem | Alternative |
|--------------|---------|-------------|
| **Monolithic docs** | Wastes tokens on irrelevant context | Modular, linked documents |
| **Narrative style** | Low information density | Declarative statements |
| **Outdated examples** | Causes agent errors | Maintain with code changes |
| **Implicit assumptions** | Agent lacks prior context | Explicit statements |
| **Over-documentation** | Diminishing returns | Focus on non-obvious information |
| **Duplicate information** | Inconsistency risk | Single source of truth with references |
| **Abstract descriptions** | Hard to act on | Concrete examples and file paths |

---

## 8. Validation Process

After creating documentation, verify quality by asking:

1. **Completeness**: Can an agent with no prior context perform common tasks?
2. **Accuracy**: Do file paths, commands, and examples work?
3. **Efficiency**: Is each document within token budget?
4. **Navigability**: Can the agent find relevant information quickly?
5. **Actionability**: Does every section lead to concrete action?

### Simulated Test

Imagine an agent receiving a task like:
- "Add a new API endpoint for user preferences"
- "Fix a bug in the payment processing module"
- "Refactor the authentication flow"

Trace through your documentation: does the agent have enough context to complete the task correctly without guessing?

---

## 9. Templates

### 9.1 Minimal AGENTS.md Template

```markdown
# [Project Name] — Agent Guide

## Quick Reference
- **Stack**: 
- **Run**: ``
- **Test**: ``
- **Build**: ``

## Project Structure
```
/src        — 
/tests      — 
/docs       — 
```

## Critical Conventions
1. 
2. 
3. 

## Before Making Changes
- [ ] Check for existing patterns in similar files
- [ ] Run tests: ``
- [ ] Follow conventions in `docs/conventions.md`

## Documentation Index
- [Architecture](./docs/architecture.md) — System design and component relationships
- [Conventions](./docs/conventions.md) — Code style and patterns
- [Tasks](./docs/tasks.md) — Step-by-step common procedures
- Domain docs (consult when working in these areas):
  - [Domain A](./docs/domains/domain-a.md)
  - [Domain B](./docs/domains/domain-b.md)
```

### 9.2 Domain Document Template

```markdown
# [Domain Name]

## Overview
[One paragraph]

## Key Files
| File | Purpose |
|------|---------|

## Data Model
```
[Schema or type definitions]
```

## Business Rules
- 

## Integration Points
- 

## Common Operations

### [Operation Name]
[Steps or code example]
```

---

## 10. Migration: CLAUDE.md to AGENTS.md

> **Temporary instruction**: Execute this migration when working in packages that have both CLAUDE.md and AGENTS.md, or only CLAUDE.md.

### Migration Steps

1. **Audit existing files**
   - Read `AGENTS.md` (if exists)
   - Read `CLAUDE.md` (if exists)

2. **Merge content**
   - Ensure `AGENTS.md` contains all important information from `CLAUDE.md`
   - `CLAUDE.md` may be outdated or not follow this guide's structure
   - Restructure merged content according to this guide's specifications

3. **Replace CLAUDE.md**
   - Delete the old `CLAUDE.md`
   - Copy the redirect template:
     ```bash
     cp /Users/mm/projects/@marianmeres/marianmeres/mm-local-docs/CLAUDE_TEMPLATE.md CLAUDE.md
     ```

4. **Verify**
   - New `CLAUDE.md` should only contain a redirect to `AGENTS.md`
   - `AGENTS.md` should be the single source of truth

### When to Skip
- Package already has redirect-style `CLAUDE.md`
- Package has no `CLAUDE.md` at all

---

## 11. Checklist for Documentation Creators

Use this checklist when creating agent documentation for a new project:

- [ ] **Entry point created** at project root (`AGENTS.md` or `CLAUDE.md`)
- [ ] **Quick reference section** includes stack, commands, and structure
- [ ] **Architecture document** explains system design and data flow
- [ ] **Conventions document** defines patterns with examples
- [ ] **Tasks document** covers common development procedures
- [ ] **Domain documents** exist for each major subsystem
- [ ] **Inline documentation** added to complex modules
- [ ] **All file paths verified** to be correct
- [ ] **All code examples tested** to ensure they work
- [ ] **Token budgets respected** for each document level
- [ ] **Cross-references validated** and not circular
- [ ] **Simulated agent test passed** for common tasks

---

*This guide should be adapted to the specific needs of each project. The goal is not rigid compliance but effective agent enablement through clear, efficient, actionable documentation.*
