# Pre-Release Documentation Update

> Ensure all documentation is current before release.

---

## 1. Detect Changes

```bash
# Files changed since last release
git diff --name-only <last-tag>..HEAD

# Commits since last release
git log --oneline <last-tag>..HEAD
```

Categorize:
- Features added/modified/removed
- Dependencies added/removed
- Env vars changed
- Schema changes

---

## 2. Update Docs

**Order**: Domain docs → Tasks → Conventions → Architecture → Entry point → README

| Change Type | Update |
|-------------|--------|
| New feature | Domain doc, AGENTS.md, README (if user-facing) |
| Modified feature | Relevant domain doc |
| Removed feature | Remove all references |
| New dependency | conventions.md or domain doc |
| New env var | README |
| Schema change | Domain doc (data model) |

For agent documentation standards, see [AGENT_DOCUMENTATION_GUIDE.md](./AGENT_DOCUMENTATION_GUIDE.md).

---

## 3. Validate

- [ ] All file paths in docs exist
- [ ] Code examples work
- [ ] Tests pass
- [ ] No references to removed features
- [ ] README setup instructions work
- [ ] New features documented

---

## 4. Summary

After updating, list:

```markdown
## Docs Updated
- [file]: [what changed]

## Flagged for Review
- [item]: [reason]
```

---

## Invocation

```
Update docs for release.
Last release: [tag]
Reference: PRE_RELEASE_DOCS_UPDATE.md
```
