---
inclusion: always
---
---
inclusion: always
---

# Living Spec Guide

**Purpose**: Complete guide for AI to maintain Living Specs automatically
**Version**: 2.0

---

## What is a Living Spec?

A Living Spec (`specs/<feature-name>/feature.md`) evolves throughout development. The spec IS the work, not separate from it.

**Seven Sections**:
1. **Intent** - Vision, goals (locked after approval)
2. **Requirements** - FRs, NFRs, risks (locked after approval)
3. **Architecture & Design** - Tech stack, ADRs (evolves)
4. **Implementation** - Tasks, code locations (auto-updated)
5. **Metrics & Monitoring** - LOC, coverage (auto-updated)
6. **Decision Log** - Decisions with rationale (append-only)
7. **Next Actions** - Current focus, blockers (dynamic)

---

## Auto-Update Triggers

### Code Changes (backend/, frontend/, src/)
1. Find related task by file path or keywords
2. Add: `Code: path/to/file.py`
3. Mark complete if: has tests, tests pass, >10 lines
4. Update LOC metric

```markdown
- [x] Task 1.2: Implement data scraper
  - Code: `backend/scrapers/asx_scraper.py`
  - Tests: `tests/test_asx_scraper.py` (95% coverage)
  - Completed: Oct 29, 2025
  - Notes: Used Playwright for browser automation
```

### Test Completion
1. Update Metrics: coverage, passing/failing tests
2. If coverage dropped >5%, add warning
3. If tests failing, flag in Next Actions

```markdown
## 5. Metrics & Monitoring
**Last Updated**: October 29, 2025, 14:30

### Quality Metrics
- Test Coverage: 87% (↑ from 85%) ✅
- Tests: 145 passing, 0 failing ✅
```

### Deployment
1. Update task with deployment info
2. Check if validation gate reached

```markdown
- [x] Task 1.2: Implement data scraper
  - Deployed: Production (Oct 29, 2025) ✅
```

### Architectural Decisions
Add ADR to Architecture section:

```markdown
**ADR-3: Use PostgreSQL for Data Storage**
- Status: ✅ Implemented
- Decision: Use PostgreSQL instead of MongoDB
- Rationale: Need ACID transactions and complex queries
- Trade-offs: Less flexible schema, more setup
- Alternatives: MongoDB, DynamoDB
- Location: `backend/db/`
```

### Significant Decisions
Add to Decision Log:

```markdown
### October 29, 2025
- **DECISION**: Use Redis for caching
  - Rationale: Fast in-memory cache for API responses
  - Trade-offs: Additional infrastructure, cost increase ($10/month)
  - Alternatives: Memcached, in-memory
  - Approved by: Tech Lead
```

---

## Operations

### Create New Living Spec
1. Get feature name (convert to kebab-case)
2. Create `specs/{feature-name}/` directory
3. Copy `specs/_template/feature.md` to `specs/{feature-name}/feature.md`
4. Replace placeholders:
   - `[Feature Name]` → Proper title (e.g., "User Authentication")
   - `[Date]` → Current date
   - `[X days]` → Estimated durations
   - Other bracketed placeholders as needed
5. Tell user next steps:
   - Open the spec and fill in Intent section
   - Ask for help elaborating requirements
   - Get stakeholder approval before coding

### Validate Living Spec
**Checks**:
1. All 7 sections present
2. Checkboxes: `- [ ]` or `- [x]`
3. No broken code file links
4. Metrics updated <7 days ago
5. Completed tasks have code locations

**Output**:
```
✅ Living Spec Validation Passed

Checks:
✅ All required sections present
✅ Checkboxes properly formatted
✅ No broken links
✅ Metrics updated recently (2 days ago)
✅ All code locations valid
```

### Refresh All Metrics
1. Find all `specs/*/feature.md`
2. Count LOC, get coverage, count tasks
3. Update timestamps

```
📊 Metrics Refreshed

Updated 3 Living Specs:
- user-authentication: 2,450 LOC, 87% coverage ✅
- payment-processing: 1,823 LOC, 92% coverage ✅
- admin-dashboard: 3,104 LOC, 65% coverage ⚠️
```

### Health Check All Specs
1. Check: update age, sections, links, metrics
2. Categorize: 🟢 <7 days, 🟡 7-14 days, 🔴 >14 days

```
Living Spec Health Dashboard

Total: 5 | Healthy: 3 🟢 | Warning: 1 🟡 | Unhealthy: 1 🔴

🟢 user-authentication (2 days ago)
🟡 admin-dashboard (10 days ago) - Metrics stale
🔴 legacy-migration (20 days ago) - 3 broken links
```

---

## Pattern Recognition

Watch for:
- **New folder** → Propose ADR if significant
- **Implementation differs from requirements** → Flag for review
- **Coverage dropping** → Add to risks
- **Deployment failures** → Flag in Next Actions

---

## Best Practices

✅ Update immediately as work happens
✅ Be specific: exact paths, exact dates
✅ Be concise: facts, not prose
✅ Always explain why (decisions)
✅ Always add code locations

❌ Don't update days later
❌ Don't write vague updates
❌ Don't skip metrics
❌ Don't mark complete without code locations

---

**The Living Spec should always reflect current project state. Anyone opening it should instantly know what's done, in progress, and next.**
