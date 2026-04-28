---
name: plan-reviewer
description: Analyze, critique, and suggest improvements to existing implementation plans. Use this skill when the user asks to "analyze this plan", "review this plan", "critique this plan", "what do you think of this plan?", "suggest improvements", "kiểm tra plan", or "phân tích plan". This skill identifies issues, risks, and opportunities to make plans stronger before execution.
---

# Plan Reviewer

Analyze existing implementation plans to identify issues, suggest improvements, and strengthen the plan before execution.

## When to Trigger

**Trigger when the user says:**
- "Analyze this plan" / "review this plan" / "critique this plan"
- "What do you think of this plan?"
- "Suggest improvements to this plan"
- "Are there any issues with this plan?"
- "Can this plan be better?"
- "Kiểm tra plan này" / "phân tích plan"
- "Check if this plan has problems"

## Workflow

### Step 1: Announce

Start with: "I'm using the plan-reviewer skill to analyze this plan."

### Step 2: Read and Understand

Read the existing `implementation_plan.md` artifact. Understand:
- The goal and scope
- The proposed changes
- The task breakdown
- Any open questions or user review items

### Step 3: Identify Issues

Analyze the plan across 6 dimensions:

| Category | What to Look For |
|----------|-----------------|
| **Completeness** | Missing steps, unclear instructions, gaps in coverage |
| **Feasibility** | Unrealistic time estimates, circular dependencies, missing prerequisites |
| **Risks** | Breaking changes, compatibility issues, edge cases not covered |
| **Order** | Tasks in wrong sequence, blockers not identified |
| **Quality** | Vague descriptions, missing verification steps |
| **Efficiency** | Redundant work, missed automation opportunities |

### Step 4: Research and Validate

For each potential issue:
- Check if assumptions are valid
- Verify file paths exist (if mentioned)
- Identify dependencies between tasks
- Look for similar patterns in the codebase

### Step 5: Present Analysis

Structure your analysis response:

```markdown
## Plan Analysis

### Summary
[1-2 sentences on overall plan quality]

### Strengths ✓
- [What works well in the plan]

### Issues Found

#### [Issue Title]
**Problem:** [What's wrong]
**Impact:** [Why it matters — risk, delay, etc.]
**Suggestion:** [How to fix it]

#### [Issue Title]
**Problem:** [What's wrong]
**Impact:** [Why it matters]
**Suggestion:** [How to fix it]

### Suggested Improvements

1. **[Improvement Name]**
   - Current: [What the plan says]
   - Improved: [What it could say]
   - Reason: [Why this is better]

2. **[Improvement Name]**
   - Current: [What the plan says]
   - Improved: [What it could say]
   - Reason: [Why this is better]

### Reordered Tasks (If Applicable)

If task order needs adjustment:
1. [Task 1] — Why first
2. [Task 2] — Why second
3. ...
```

### Step 6: Request Next Steps

Present the analysis and ask:

> **Analysis complete.** Here are my findings:
>
> - **X issues identified** that could cause problems
> - **Y suggestions** to make the plan stronger
>
> **What would you like me to do?**
> - ✅ **Update the plan** — Apply the suggested improvements
> - ❌ **Keep as is** — Proceed with current plan
> - ❌ **Cancel** — Abandon this plan

## Examples

### Example 1: Finding Missing Steps

**User:** "Check this plan for any issues"

**Assistant:**
> "I'm using the plan-reviewer skill to analyze this plan."
>
> [Reads the plan, identifies missing verification steps, unrealistic time estimates]
>
> [Presents analysis with specific issues and suggestions]
>
> **Analysis complete.** X issues identified...

### Example 2: Task Order Problem

**User:** "Can you review the order of tasks in this plan?"

**Assistant:**
> "I'm using the plan-reviewer skill to analyze this plan."
>
> [Identifies that database migration should come before API changes]
>
> [Proposes reordered task sequence with justification]
>
> **Analysis complete.** Task order issue found...

## Common Mistakes to Watch For

| ❌ Avoid | ✅ Look For |
|----------|------------|
| Being too vague about issues | Specific, actionable suggestions |
| Ignoring task dependencies | Clear blocker identification |
| Missing verification steps | Comprehensive testing plan |
| Over-engineering | Appropriate scope for the task |

## Key Principles

1. **Be constructive** — Every issue should come with a suggestion
2. **Prioritize impact** — Focus on issues that affect success most
3. **Preserve intent** — Don't change what the user wants to achieve
4. **Explain why** — Help user understand the reasoning behind suggestions
