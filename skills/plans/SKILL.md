---
name: plans
description: Create and update implementation plans as artifacts without premature execution. Use this skill whenever the user asks to create a plan, write a plan, make a plan, update a plan, or when you need to think through an implementation approach before starting. Also triggers when user uses the /plans slash command. This skill creates implementation_plan.md artifacts following writing-plans structure and STOPS after plan creation - it does NOT execute until the user explicitly approves the plan. Critical: do NOT start executing when the user asks for a plan. Create the plan artifact and wait for approval.
---

# Artifact Plans

Create implementation plans as artifacts. Stop after plan creation and wait for user approval before any execution.

## When to Use

**Trigger this skill when:**
- User says "create a plan", "write a plan", "make a plan", "lập kế hoạch", "tạo kế hoạch"
- User says "plan for this", "plan out", "plan the implementation"
- User uses the `/artifact-plans` slash command
- User asks to "update the plan" or "revise the plan"
- User has requirements/specs for a multi-step task
- You detect the task requires architectural changes, extensive research, or multi-step implementation
- User mentions planning-related phrases in any language

**CRITICAL BEHAVIOR:**
- When user asks for a plan → Create the plan artifact ONLY
- Do NOT start executing after creating the plan
- Do NOT write any code before user approves the plan
- Wait for explicit user approval before proceeding to execution

## Plan Creation Workflow

### 1. Announce Your Intent

Start with: "I'm using the artifact-plans skill to create the implementation plan."

### 2. Determine Scope

Assess if the task needs planning:
- Multi-step implementation
- Architectural decisions
- Multiple files/components
- Unknown requirements or edge cases
- Complex changes

If the task is simple (one-off edit, fix syntax error, add comment), you may not need a full plan. But if the user explicitly asks for a plan, create one.

### 3. Create the Implementation Plan

Write a comprehensive implementation plan following this structure:

```markdown
# [Feature Name] Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use artifact-plans for implementation. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** [One sentence describing what this builds]

**Architecture:** [2-3 sentences about approach]

**Tech Stack:** [Key technologies/libraries]

---

## Proposed Changes

[Group files by component, order logically - dependencies first]

### [Component Name]

[Summary of what will change]

#### [MODIFY] [file basename](file:///absolute/path/to/file)
#### [NEW] [file basename](file:///absolute/path/to/newfile)
#### [DELETE] [file basename](file:///absolute/path/to/deletedfile)

## User Review Required

[Document anything requiring user feedback - breaking changes, significant design decisions]

> [!IMPORTANT]
> Essential requirements or must-know information

> [!WARNING]
> Breaking changes or compatibility issues

> [!CAUTION]
> High-risk actions that could cause issues

## Open Questions

[Any clarifying questions for the user that impact the implementation]

## Verification Plan

### Automated Tests
- [Test commands to run]

### Manual Verification
- [Steps for human testing]

## Task Breakdown

### Task 1: [Task Name]

- [ ] **Step 1: [Action description]**
- [ ] **Step 2: [Action description]**
- [ ] **Step 3: [Action description]**

### Task 2: [Task Name]

- [ ] **Step 1: [Action description]**
- [ ] **Step 2: [Action description]**
- [ ] **Step 3: [Action description]**
```

### 4. Save as Artifact

Save the plan as `implementation_plan.md` in the conversation artifacts directory:
- Path: `<appDataDir>\brain\<conversation-id>\implementation_plan.md`
- Use the write_to_file tool with `IsArtifact: true`

### 5. Request User Approval

After creating the plan, explicitly ask:

**"Plan complete. The implementation plan has been created as an artifact.**

**Review the plan and let me know:**
- ✅ **Approve and execute** - I'll start implementing
- ❌ **Request changes** - Tell me what to modify
- ❌ **Cancel** - Don't proceed with this plan"

**Wait for explicit approval before any execution.**

## Plan Structure Guidelines

### Use writing-plans structure as reference

The plan should follow the structure defined in the writing-plans skill:
- Clear goal statement
- Architecture overview
- File mapping before tasks
- Bite-sized task granularity (each step = 2-5 minutes)
- No placeholders - complete details in every step
- Self-review checklist

### File Structure

Map files before defining tasks:
- Design units with clear boundaries
- Exact file paths always
- Files that change together should live together
- Follow established patterns in existing codebase

### Task Granularity

Each step should be:
- One atomic action
- 2-5 minutes to complete
- Can be verified independently

Example task structure:
```markdown
### Task 1: User Authentication

- [ ] **Step 1: Add user model**
- [ ] **Step 2: Write login endpoint**
- [ ] **Step 3: Add JWT validation**
- [ ] **Step 4: Test the flow**
```

## Updating Plans

When user asks to update a plan:

1. view_file the existing `implementation_plan.md`
2. Identify what needs to change
3. Make targeted edits (do not rewrite entirely)
4. Save the updated plan
5. Re-request approval if scope changed significantly

## Common Mistakes to Avoid

| ❌ DON'T | ✅ DO |
|----------|-------|
| Create plan then start coding | Create plan then WAIT for approval |
| "I'll do this while creating the plan" | Write complete plan first |
| Partial plan with "I'll fill in later" | Complete plan with all details |
| Auto-execute after plan creation | Explicit user approval required |

## Example Conversation Flow

**User:** "Create a plan to add dark mode to the app"

**Assistant:** 
1. "I'm using the artifact-plans skill to create the implementation plan."
2. [Analyzes requirements, maps files, breaks down tasks]
3. Creates `implementation_plan.md` artifact
4. "Plan complete. The implementation plan has been created...

**User:** "Looks good, proceed"

**Assistant:**
5. [Begins execution - now it's appropriate to start]

**OR**

**User:** "Can you adjust the task order?"

**Assistant:**
5. Updates the plan accordingly
6. Re-requests approval

## Key Principles

1. **Plan ≠ Execute** - Planning is a separate phase
2. **Complete details** - No placeholders, no TODOs
3. **User in control** - Explicit approval required before execution
4. **Iterative refinement** - User can request changes to plan
5. **Bite-sized tasks** - Each step verifiable independently
