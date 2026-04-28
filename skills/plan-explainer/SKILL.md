---
name: plan-explainer
description: Explain implementation plans — what they are, what each section means, and how to read them. Use this skill when the user asks to "explain this plan", "what does this section mean?", "giải thích plan", "hiểu plan", "what's in this plan?", or needs help understanding an existing implementation plan. This skill helps demystify plans for users who are new to planning workflows.
---

# Plan Explainer

Help users understand implementation plans by explaining structure, sections, and terminology in plain language.

## When to Trigger

**Trigger when the user:**
- Asks to "explain this plan" or "what's in this plan?"
- Asks about specific sections ("what does 'Proposed Changes' mean?")
- Is confused about plan structure or format
- Asks "giải thích plan" / "hiểu plan" / "plan là gì"
- Says "I don't understand this part"
- Wants a walkthrough of a plan

## Workflow

### Step 1: Identify the Request

Determine what the user needs:

| User Says... | They Need... |
|--------------|--------------|
| "Explain this plan" | Full plan overview |
| "What does X mean?" | Specific section explanation |
| "How do I read this?" | Reading guide |
| "What should I look for?" | Plan evaluation guidance |
| "Why is this structured this way?" | Rationale behind format |

### Step 2: Provide Context-Relevant Explanation

Based on what they're asking about:

#### If they want the full plan explained:

```
## Plan Overview

This plan has [X] main sections:

1. **Title** — What this plan is about
2. **Goal** — What we're trying to achieve (one sentence)
3. **Why Planning Helps** — Why this task benefits from planning upfront
4. **Current State** — What's in place today (if relevant)
5. **Proposed Changes** — Exactly what files will change
6. **Architecture** — How the pieces fit together
7. **User Review Required** — Decisions that need your input
8. **Open Questions** — Things still being figured out
9. **Task Breakdown** — Step-by-step implementation
10. **Verification** — How we confirm it works
```

#### If they ask about a specific section:

Use plain language, avoid jargon. Provide:
- **What it is** — simple definition
- **Why it's there** — purpose and value
- **What to look for** — how to evaluate it

### Step 3: Answer Follow-up Questions

Be ready for:
- "What happens if I don't approve this?"
- "Do I need to understand everything?"
- "Can I ask for changes before approving?"
- "What's the difference between X and Y?"

### Step 4: Adjust Explanation Level

Match the user's familiarity:

| User Shows... | Adjust By... |
|---------------|-------------|
| Technical background | Use technical terms, explain nuances |
| New to planning | Use analogies, simpler language |
| Specific question | Answer directly, don't over-explain |
| General confusion | Start from basics, build up |

## Section-by-Section Guide

### Title / Feature Name
**What:** The name of what we're building
**Why:** Gives context for everything else
**Read for:** Is this what you want to build?

### Goal
**What:** One sentence describing the outcome
**Why:** Keeps everyone aligned on the end goal
**Read for:** Does this match your expectation?

### Why Planning Helps
**What:** Brief explanation of planning value
**Why:** Helps you understand why we took time to plan
**Read for:** Is the effort justified?

### Current State
**What:** What exists today (relevant parts)
**Why:** Grounds the work in reality
**Read for:** Do we understand the starting point?

### Proposed Changes
**What:** Exact list of files being modified/added/deleted
**Why:** You know exactly what will change
**Read for:** Are these the right files? Missing anything?

### Architecture
**What:** High-level approach (2-3 sentences)
**Why:** Shows how components connect
**Read for:** Does this approach make sense?

### User Review Required
**What:** Decisions that need your input
**Why:** These are choices, not facts
**Read for:** Do you agree with these decisions?

### Open Questions
**What:** Things still being clarified
**Why:** Identifies unknowns upfront
**Read for:** Are these blockers? Can you help answer?

### Task Breakdown
**What:** Step-by-step implementation with checkboxes
**Why:** Makes large work manageable
**Read for:** Are the steps logical? Time estimates reasonable?

### Verification
**What:** How we confirm the work is done correctly
**Why:** Ensures quality before declaring success
**Read for:** Will this catch problems?

## Common Questions (and Answers)

### "Do I need to understand every section?"

Not necessarily. Focus on:
- **Goal** — Must understand, it's the destination
- **Proposed Changes** — Must review, it's what affects your code
- **User Review Required** — Must decide on, it's what needs your input

The rest are details you can trust or skim.

### "What if I don't understand something?"

Just ask! Examples:
- "What does '[MODIFY]' mean?" → "It means we're editing this existing file"
- "Why is there a 'User Review Required' section?" → "That's where we flag anything that needs your decision..."

### "Can I approve part of the plan?"

Yes! You can:
- Approve certain tasks, request changes on others
- Ask to break a large task into smaller approvals
- Request more information before deciding on specific sections

### "What's the difference between 'task' and 'step'?"

- **Task** = A unit of work (e.g., "Add dark mode")
- **Step** = Individual actions within that task (e.g., "Update CSS", "Test in browser")

## Key Principles

1. **Plain language** — Avoid jargon, use analogies when helpful
2. **Answer what they ask** — Don't over-explain or under-explain
3. **Be patient** — First-time plan readers may need basics
4. **Invite questions** — "What else would you like explained?"
5. **Match their level** — Technical users want details, others want simplicity
