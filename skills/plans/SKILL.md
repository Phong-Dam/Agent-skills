---
name: plans
description: Router skill that orchestrates plan-related workflows by delegating to focused sub-skills. Use this skill when the user wants to work with implementation plans — whether creating, analyzing, reviewing, updating, or explaining them. This skill detects user intent and delegates to the appropriate sub-skill (plan-creator, plan-reviewer, plan-updater, or plan-explainer). Always triggers when user mentions planning-related requests in any language.
---

# Plans Skill

Router skill that orchestrates plan-related workflows by delegating to focused sub-skills.

## Overview

This skill coordinates plan-related tasks by:
1. Detecting user intent
2. Delegating to the appropriate sub-skill
3. Ensuring smooth handoff and consistent plan format

The sub-skills handle specific concerns:
- **plan-creator** — Create new implementation plans from scratch
- **plan-reviewer** — Analyze, critique, and suggest improvements to existing plans
- **plan-updater** — Update and refine existing plans based on feedback
- **plan-explainer** — Explain plan structure and help users understand plans

## When to Trigger

**Always trigger when user wants to work with plans:**
- "Create a plan", "make a plan", "lập kế hoạch", "tạo kế hoạch"
- "Analyze this plan", "review this plan", "critique this plan", "kiểm tra plan"
- "Update the plan", "modify the plan", "revise the plan"
- "Suggest improvements to this plan"
- "What do you think of this plan?"
- "Explain this plan", "what does this mean?", "giải thích plan"

## Intent Detection

### Create New Plan
**Keywords:** create plan, make plan, write plan, lập kế hoạch, tạo kế hoạch, plan for, plan this out

**→ Delegate to plan-creator skill**

### Analyze/Review Existing Plan
**Keywords:** analyze plan, review plan, critique, check plan, phân tích plan, kiểm tra plan

**→ Delegate to plan-reviewer skill**

### Update/Modify Existing Plan
**Keywords:** update plan, modify plan, revise plan, change the plan, edit the plan

**→ Delegate to plan-updater skill**

### Explain/Understand Existing Plan
**Keywords:** explain plan, what does this mean, giải thích plan, hiểu plan, what's in this plan, help me understand this

**→ Delegate to plan-explainer skill**

## Workflow

### Step 1: Identify Intent

Quickly determine what the user wants:
- Create new plan? → plan-creator
- Analyze existing plan? → plan-reviewer
- Update existing plan? → plan-updater
- Understand/explain a plan? → plan-explainer

### Step 2: Delegate

Call the appropriate sub-skill with clear context:
```
I'm using the [sub-skill-name] skill to [action].
```

### Step 3: Coordinate (If Needed)

If user feedback spans multiple concerns:
- Combine outputs from relevant sub-skills
- Ensure consistent plan format across skills
- Maintain plan artifact in same location

## Shared Plan Template

All sub-skills use this consistent format:

```markdown
# [Feature Name] Implementation Plan

**Goal:** [One sentence describing what this builds]

**Why Planning Helps:** [1-2 sentences on why this benefits from planning]

---

## Proposed Changes

### [Component Name]
[Summary of what changes]

#### [MODIFY] [file basename](file:///path/to/file)
#### [NEW] [file basename](file:///path/to/newfile)
#### [DELETE] [file basename](file:///path/to/deletedfile)

## Task Breakdown

### Task 1: [Task Name]
- [ ] **Step 1: [Action]** [2-5 min]
- [ ] **Step 2: [Action]** [2-5 min]

### Task 2: [Task Name]
- [ ] **Step 1: [Action]** [2-5 min]

## Verification

### Automated Tests
- [Test commands]

### Manual Verification
- [Steps]

## Open Questions
[Any clarifications needed]
```

## Key Principles

1. **Router ≠ Execute** — Delegate to sub-skills, don't execute directly
2. **Clear intent** — Identify user's goal before delegating
3. **Consistent output** — All sub-skills use same plan format
4. **Seamless handoff** — User shouldn't notice skill transitions
