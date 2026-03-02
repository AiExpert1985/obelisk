---
description: Creates and implements an Obelisk task
---

## Context

Read before starting:
- `/obelisk/contracts/contracts-summary.md`
- `/obelisk/design/design-summary.md`
- `/obelisk-core/guidelines/ai-engineering.md`

If any missing → STOP. Output: Use `/init-project` to initialize the project.

---

## DISCOVERY — Mandatory

Discovery is never skippable. Before presenting the task summary you MUST:
- Surface all non-trivial assumptions
- Ask clarifying questions on anything that would change execution

Inference from contracts, design, and existing patterns is allowed.
All non-trivial assumptions must be confirmed before proceeding.

Do NOT ask about:
- Anything inferable from context, contracts, or design
- Implementation details you can decide yourself
- Low-impact edge cases

If a contract conflict is detected:
```markdown
⚠️ Contract Conflict
Conflicts with: "[exact contract text]"
Options: 1. Adjust task  2. Update contract
Recommendation: [option + reason]
```

If the task introduces a new business-critical rule:
```markdown
📋 New Contract
Rule: [what it is and why it matters]
Add? yes/no
```

## Discovery Output Format

No narration. No thinking out loud. No filler.

**Assumptions:** [assumption] — [basis]
**Questions:**
1. [question]
   Recommendation: [option] — [reason]

If no questions exist: state "No clarifications needed" and list assumptions only.
Do not proceed to Task Summary until assumptions are confirmed.

## Task Summary
```markdown
Task Summary

Goal: [what and why]
Scope: ✓ [included] / ✗ [excluded]
Approach: [key design decisions]
Assumptions: [confirmed, or "None"]
Contracts: [new or changed, or "None"]
Constraints: [limits implementation must respect]
Risks: [known risks or "None"]
```

After presenting — STOP. Do not proceed. Do not write code.
Wait for corrections or `implement`.
If corrections received, update summary and STOP again.
Only proceed when `implement` is received.

---

## IMPLEMENTATION

Implement the agreed task. During implementation:
- Follow the agreed task summary
- Follow `/obelisk-core/guidelines/ai-engineering.md`
- Respect `/obelisk/contracts/contracts-summary.md` and `/obelisk/design/design-summary.md`

For any follow-up request or scope change from the user:
- Treat it like a mini-discovery: understand the change, check it against contracts and design, surface conflicts if any, confirm understanding before proceeding
- Do not implement changes blindly

When done, output:

```markdown
Implementation complete. Enter `@archive-task` to archive.
```