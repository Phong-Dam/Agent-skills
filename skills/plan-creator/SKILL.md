---
name: plan-creator
description: Create detailed implementation plans as structured artifacts, then STOP and wait for approval before any execution. Use this skill whenever the user asks to "create a plan", "write a plan", "make a plan", "lập kế hoạch", "tạo kế hoạch", "plan this out", or "think through the implementation". This skill is especially valuable for complex multi-step tasks involving architectural changes, multiple file modifications, research requirements, or unclear requirements. CRITICAL: Always create the plan as an artifact and WAIT for explicit approval — never auto-execute.
---

# Plan Creator

Create comprehensive implementation plans as artifacts. Planning is a distinct phase from execution — always complete the plan and obtain user approval before writing any code.

## When to Trigger

**Always trigger when the user:**
- Explicitly requests a plan ("create a plan", "write a plan", "lập kế hoạch")
- Uses planning keywords ("plan this out", "think through", "approach")
- Has a multi-step or complex task

**Trigger proactively when you detect:**
- Architectural changes or refactoring work
- Multiple files need modification
- Unclear requirements or edge cases
- The task involves research before implementation

> **Note:** If the task is genuinely simple (fix a typo, run one command), you may not need this skill. But if the user explicitly asks for a plan, create one regardless.

## Workflow

### Step 1: Announce

Start with: "I'm using the plan-creator skill to create the implementation plan."

### Step 2: Assess Scope

Quickly determine if the task needs detailed planning:

| Consider Planning If... | Likely Too Simple If... |
|------------------------|-------------------------|
| Multiple files/components | Single file edit |
| Architectural decisions | Straightforward change |
| Unknown requirements | Clear specifications |
| 5+ steps required | 1-3 quick steps |

If the user explicitly asked for a plan, proceed regardless of scope.

### Step 3: Research (When Needed)

For complex tasks, research first:
- Examine existing codebase structure
- Identify dependencies and patterns
- Check for similar implementations
- Find files that will need modification

### Step 4: Create the Implementation Plan

Write the plan following this structure:

```markdown
# [Feature Name] Implementation Plan

**Goal:** [One sentence describing what this builds]

**Why Planning Helps:** [1-2 sentences on why this benefits from planning upfront]

---

## Current State

[What exists today, if anything relevant]

## Proposed Changes

### [Component Name]

[Summary of what will change]

#### [MODIFY] [file basename](file:///absolute/path/to/file)
#### [NEW] [file basename](file:///absolute/path/to/newfile)
#### [DELETE] [file basename](file:///absolute/path/to/deletedfile)

## Architecture

[2-3 sentences on the approach]

## User Review Required

[Anything requiring user feedback — breaking changes, design decisions, open questions]

> [!IMPORTANT]
> Essential requirements

> [!WARNING]
> Breaking changes

> [!CAUTION]
> High-risk actions

## Open Questions

[Any clarifying questions for the user]

---

## Task Breakdown

### Task 1: [Task Name]

- [ ] **Step 1: [Action]** [2-5 min]
- [ ] **Step 2: [Action]** [2-5 min]
- [ ] **Step 3: [Action]** [2-5 min]

### Task 2: [Task Name]

- [ ] **Step 1: [Action]** [2-5 min]
- [ ] **Step 2: [Action]** [2-5 min]

## Verification

### Automated Tests
- [Test commands to run]

### Manual Verification
- [Steps for human testing]
```

**Why this structure matters:**
- **Goal** gives context for all decisions
- **Why Planning Helps** explains the value upfront
- **Current State** grounds the work in reality
- **Proposed Changes** maps exactly what files are affected
- **Task Breakdown** uses checkboxes with time estimates
- **Verification** ensures quality before declaring done

### Step 5: Save as Artifact

Save the plan to the conversation artifacts directory:
- Path: `<appDataDir>\brain\<conversation-id>\implementation_plan.md`
- Use write_to_file with `IsArtifact: true`

### Step 6: Request Approval

Present the plan and explicitly ask:

> **Plan complete.** The implementation plan has been created as an artifact.
>
> **Review the plan and let me know:**
> - ✅ **Approve and execute** — I'll start implementing
> - ❌ **Request changes** — Tell me what to modify
> - ❌ **Cancel** — Don't proceed with this plan

**Wait for explicit approval. Do not execute. Do not write code.**

## Examples

### Example 1: Adding Dark Mode

**User:** "Create a plan to add dark mode to the app"

**Assistant:**
> "I'm using the plan-creator skill to create the implementation plan."
>
> [Analyzes codebase, identifies theme files, CSS variables]
>
> [Creates implementation_plan.md]
>
> **Plan complete.** The implementation plan has been created...

### Example 2: Refactoring a Module

**User:** "We need to refactor the auth module to support OAuth"

**Assistant:**
> "I'm using the plan-creator skill to create the implementation plan."
>
> [Examines current auth implementation, researches OAuth patterns]
>
> [Creates implementation_plan.md]
>
> **Plan complete.** The implementation plan has been created...

## Common Mistakes

| ❌ Don't | ✅ Do |
|----------|-------|
| Create plan then start coding | Create plan then WAIT |
| "I'll fill in details later" | All details upfront |
| Auto-execute after plan | Explicit approval required |
| Generic steps | Specific, contextualized steps |

## Key Principles

1. **Plan ≠ Execute** — Planning and execution are separate phases
2. **Complete details** — No placeholders, no TODOs in the plan itself
3. **User in control** — Explicit approval required before any code
4. **Bite-sized steps** — Each step verifiable independently (2-5 minutes)
5. **Time estimates** — Help user understand effort and sequencing
