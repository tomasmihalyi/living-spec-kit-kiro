# Living Spec Kit - Complete Guide

This guide is a complete living spec kit with all the features and best practices. It's designed to help you get started with Living Specs quickly and efficiently.

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Creating Living Specs](#creating-living-specs)
4. [Working with Living Specs](#working-with-living-specs)
5. [Common Operations](#common-operations)
6. [Best Practices](#best-practices)
7. [Troubleshooting](#troubleshooting)
8. [Advanced Features](#advanced-features)

---

## Introduction

### What is a Living Spec?

A Living Spec is a single markdown file that evolves throughout your project's lifecycle. Unlike traditional documentation that becomes stale, a Living Spec is maintained by Kiro AI when you ask.

### Key Benefits

- **Minimal overhead** - Just ask Kiro when you need updates
- **Fast onboarding** - New team members read the spec
- **Zero drift** - Specs stay current with code
- **Complete traceability** - Decisions and changes documented
- **No dependencies** - Just Kiro AI + 2 files

### How It Works

1. You create a Living Spec for your feature (ask Kiro)
2. You fill in the Intent and Requirements
3. You start coding
4. You ask Kiro to update the spec when needed
5. The spec stays current with your code

---

## Installation

### Simple Installation

```bash
# Navigate to your project
cd /path/to/your/project

# Copy steering rules
mkdir -p .kiro/steering
cp living-spec-kit/.kiro/steering/living-spec.md .kiro/steering/

# Copy template
mkdir -p specs/_template
cp living-spec-kit/specs/_template/feature.md specs/_template/
```

### Verify Installation

```bash
# Check steering file
ls .kiro/steering/living-spec.md

# Check template
ls specs/_template/feature.md
```

**Done!** You now have Living Spec support.

---

## Creating Living Specs

### Create a New Spec

Ask Kiro:
```
"Create a Living Spec for user-authentication"
```

Kiro will:
1. Create `specs/user-authentication/` directory
2. Copy template to `specs/user-authentication/feature.md`
3. Replace placeholders with actual values
4. Create a README with quick links
5. Tell you next steps

### Fill in the Intent

Open the created spec and complete the Intent section:

```markdown
## 1. Intent

### Vision
Build a secure user authentication system that supports JWT tokens and OAuth2

### Goals
- [ ] Secure user authentication
- [ ] Support multiple auth methods
- [ ] Fast and reliable

### Success Criteria
- [ ] 99.9% uptime
- [ ] <500ms auth response time
- [ ] Zero security incidents
```

### Elaborate Requirements

Ask Kiro to help:
```
"Please elaborate requirements for the user-authentication Living Spec"
```

Kiro will:
1. Ask clarifying questions
2. Generate functional requirements
3. Identify non-functional requirements
4. List potential risks
5. Propose implementation units

### Lock Sections

After stakeholder approval:
1. Mark Intent as "Locked"
2. Mark Requirements as "Approved - [Date]"
3. These sections won't change without formal process

---

## Working with Living Specs

### The Seven Sections

1. **Intent** (Locked) - Your north star
2. **Requirements** (Approved) - What to build
3. **Architecture** (Evolves) - How to build it
4. **Implementation** (Auto-updated) - Tasks and progress
5. **Metrics** (Auto-updated) - Current state
6. **Decision Log** (Append-only) - Why decisions were made
7. **Next Actions** (Dynamic) - What's next

### Implementation Section

Tasks are organized into Units:

```markdown
### Unit 1: Authentication 🟡 IN PROGRESS

- [x] Task 1.1: Setup JWT library
  - Code: `backend/auth/jwt.py`
  - Tests: `tests/test_jwt.py`
  - Completed: Oct 29, 2025
  
- [ ] Task 1.2: Implement login endpoint
  - Estimated: 1 day
  - Dependencies: Task 1.1
```

### Validation Gates

After each Unit, validate before proceeding:

```markdown
#### Validation Gate 1
- [ ] All tasks complete
- [ ] Tests passing (>70% coverage)
- [ ] Cost within budget
- [ ] Stakeholder approval
```

---

## Common Operations

### Update Spec After Coding

After you write code, ask Kiro:
```
"Update the user-authentication Living Spec with my recent changes"
```

Kiro will:
1. Find related tasks in the spec
2. Add code locations
3. Mark tasks complete if appropriate
4. Update metrics

### Refresh Metrics

Weekly or after major changes, ask Kiro:
```
"Refresh metrics for all Living Specs"
```

Kiro will:
1. Count lines of code
2. Get test coverage
3. Count completed tasks
4. Update timestamps

### Validate Spec

Before committing, ask Kiro:
```
"Validate the user-authentication Living Spec"
```

Kiro will check:
1. All required sections present
2. Checkboxes properly formatted
3. No broken links to code files
4. Metrics updated recently
5. Completed tasks have code locations

### Health Check All Specs

Periodically, ask Kiro:
```
"Run health check on all Living Specs"
```

Kiro will report:
- Total specs
- Healthy (🟢), Warning (🟡), Unhealthy (🔴)
- Issues found
- Actions needed

### Log a Decision

When making significant decisions, ask Kiro:
```
"Add to decision log: We chose PostgreSQL over MongoDB because we need ACID transactions for financial data"
```

Kiro will add to the Decision Log section with:
- Date
- What was decided
- Rationale
- Trade-offs
- Alternatives considered

---

## Best Practices

### Do's ✅

- **Create one spec per major feature**
- **Fill in Intent before coding**
- **Get requirements approved before implementation**
- **Use validation gates religiously**
- **Log all significant decisions**
- **Ask Kiro to update specs regularly**

### Don'ts ❌

- **Don't skip the Intent section**
- **Don't change locked sections without approval**
- **Don't skip validation gates**
- **Don't ignore warnings**
- **Don't let metrics go stale**

### Workflow

1. **Inception**: Create spec, elaborate requirements, get approval
2. **Construction**: Code and ask Kiro to update spec
3. **Validation**: Review at gates, approve before proceeding
4. **Operations**: Monitor metrics, track incidents

---

## Troubleshooting

### Kiro Doesn't Understand Living Spec Commands

**Check**:
```bash
ls .kiro/steering/living-spec.md
```

**Fix**:
If missing, copy the steering file from the kit.

### Template Not Found

**Check**:
```bash
ls specs/_template/feature.md
```

**Fix**:
If missing, copy the template from the kit.

### Spec Updates Not Happening

**Reality**:
Living Specs require manual invocation. You need to ask Kiro to update them.

**Solution**:
After making changes, ask Kiro:
```
"Update the Living Spec with my recent changes"
```

For true automation, you'd need to set up agent hooks through Kiro's UI.

### Validation Issues

**Common Issues**:
- Missing required sections
- Invalid checkbox format
- Broken links to code files
- Stale metrics

**Fix**:
Ask Kiro to validate and it will tell you what needs fixing:
```
"Validate the Living Spec"
```

---

## Advanced Features

### Multiple Specs

Create one spec per major feature by asking Kiro:

```
"Create a Living Spec for authentication"
"Create a Living Spec for payment-processing"
"Create a Living Spec for admin-dashboard"
```

### Customize the Template

Edit `specs/_template/feature.md` to match your team's needs:
- Add custom sections
- Change the structure
- Add team-specific prompts
- Modify metrics tracked

### Customize AI Behavior

Edit `.kiro/steering/living-spec.md` to change how Kiro maintains specs:
- Modify update patterns
- Change validation rules
- Add custom operations
- Adjust communication style

---

## What Makes This Different

**Traditional approach**:
- Bash scripts with external dependencies
- Complex JSON configurations
- Hook implementations to maintain
- Brittle automation

**Living Spec Kit v2.0**:
- Two files (steering + template)
- Zero external dependencies
- Natural language commands
- Intelligent AI automation

---

## Additional Documentation

- **Integration Guide**: `INTEGRATION_GUIDE.md` - Detailed setup and integration
- **Overview**: `OVERVIEW.md` - Living Spec concept and philosophy
- **Template**: `specs/_template/feature.md` - See the structure

---

## Summary

Living Specs provide:
- **AI-guided maintenance** - Kiro updates when you ask
- **Zero drift** - Specs stay current with code
- **Instant visibility** - Status at a glance
- **Validation** - Quality assurance built-in
- **Decision capture** - Historical context preserved

**Result**: Minimal overhead, fast onboarding, always-current documentation.

---

*Two files. Zero dependencies. Intelligent automation.*

