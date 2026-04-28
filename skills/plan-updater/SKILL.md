---
name: plan-updater
description: Update and refine existing implementation plans based on user feedback or changing requirements. Use this skill when the user asks to "update the plan", "modify the plan", "revise the plan", "change the plan", or wants to adjust an existing implementation plan. This skill handles targeted edits, scope changes, and plan evolution while maintaining structure.
---

# Plan Updater

Update and refine existing implementation plans based on feedback or changing requirements.

## When to Trigger

**Trigger when the user says:**
- "Update the plan" / "modify the plan" / "revise the plan"
- "Change the plan" / "edit the plan"
- "Adjust this plan" / "refine this plan"
- "Add more details to the plan"
- "Remove X from the plan"
- "Reorder the tasks"
- "Make the plan simpler/more detailed"
- "Cập nhật plan" / "sửa plan"

## Workflow

### Step 1: Announce

Start with: "I'm using the plan-updater skill to update the implementation plan."

### Step 2: Read Current Plan

Read the existing `implementation_plan.md` to understand:
- Current structure and sections
- What needs to change
- What should remain unchanged

### Step 3: Understand the Request

Clarify if needed:
- What specifically should change?
- What's the reason for the change?
- Any new requirements to incorporate?

### Step 4: Make Targeted Edits

Update the plan with specific changes:

**Types of updates:**

| Update Type | How to Handle |
|-------------|---------------|
| **Add new task** | Insert in appropriate location with time estimate |
| **Remove task** | Delete and renumber remaining tasks |
| **Reorder tasks** | Move tasks and update sequence |
| **Change step** | Edit specific step description |
| **Add file** | Add to Proposed Changes section |
| **Remove file** | Remove from Proposed Changes |
| **Change scope** | Update Goal, add/remove tasks accordingly |
| **Fix issue** | Address specific problem identified |

**Preserve these elements:**
- Overall plan structure
- Already-approved sections
- Consistent formatting

### Step 5: Present Updated Plan

Show the changes made:

```markdown
## Plan Updates Applied

### Changes Made

1. **[Change 1]**
   - Before: [original]
   - After: [updated]

2. **[Change 2]**
   - Before: [original]
   - After: [updated]

### Updated Task Breakdown

[Show updated task list with changes highlighted]

---

[Full updated plan content]
```

### Step 6: Re-request Approval

> **Plan updated.** Here are the changes:
>
> - Change 1: ...
> - Change 2: ...
>
> **Review the updated plan and let me know:**
> - ✅ **Approve and execute** — I'll start implementing
> - ❌ **Request more changes** — Tell me what else to modify
> - ❌ **Cancel** — Keep the original plan
>
> If scope changed significantly, the plan may need re-review before execution.

## Update Patterns

### Pattern 1: Task Reordering

```
1. Identify current order
2. Determine logical new order (dependencies, priority)
3. Move tasks in list
4. Update numbering
5. Add note explaining new order
```

### Pattern 2: Adding New Requirements

```
1. Add to Goal if scope expansion
2. Add new files to Proposed Changes
3. Add new tasks to Task Breakdown
4. Add verification if needed
5. Add to Open Questions if needs clarification
```

### Pattern 3: Simplifying Plan

```
1. Identify non-essential tasks
2. Remove or merge similar steps
3. Combine related small tasks
4. Update time estimates
5. Preserve core requirements
```

### Pattern 4: Handling Breaking Changes

If update fundamentally changes the plan:
1. Acknowledge the change scope
2. Suggest plan-reviewer for re-analysis
3. Request fresh approval
4. Document what changed and why

## Examples

### Example 1: Change Task Order

**User:** "Can you do the database work before the API work?"

**Assistant:**
> "I'm using the plan-updater skill to update the implementation plan."
>
> [Reorders tasks: Database → API]
>
> **Plan updated.**
> - Task 1: Database migration (moved first)
> - Task 2: API changes (moved second)

### Example 2: Add New Requirement

**User:** "We also need to add unit tests for the new feature"

**Assistant:**
> "I'm using the plan-updater skill to update the implementation plan."
>
> [Adds verification tests task]
>
> **Plan updated.**
> - Added Task 3: Add unit tests

### Example 3: Remove Overly Complex Step

**User:** "The deployment section is too complex, simplify it"

**Assistant:**
> "I'm using the plan-updater skill to update the implementation plan."
>
> [Simplifies 5 steps into 2 essential ones]
>
> **Plan updated.**
> - Consolidated deployment to 2 steps

## Key Principles

1. **Targeted edits** — Change only what's needed, preserve the rest
2. **Preserve structure** — Maintain consistent plan format
3. **Explain changes** — Show before/after so user understands
4. **Re-approval** — Always re-request approval after changes
5. **Document rationale** — Note why changes were made
