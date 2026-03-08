---
description: Compact log and regenerate contracts summary
---
## Required Files

- `/obelisk/history/history-log.md`
- `/obelisk/contracts/contracts-summary.md`

If any file is missing → STOP. Output: Use `@init-project` to initialize the project.

---

## Source of Truth

`history-log.md` is the sole source of truth.
Entries are ordered oldest → newest. Later entries may add, refine, or replace earlier ones.
Read the entire file before generating summaries.
Only **Contracts** fields are used for summaries.

---

## Regenerate Contracts Summary

Extract all **Contracts** fields from history-log entries.

- Keep only active invariants — if a later entry updates a rule, keep the latest version
- Merge contracts expressing the same invariant without altering meaning
- If a contract is declared but not enforced in code → mark "Active but unenforced"
- If conflict is unclear → keep both and flag
- Do NOT invent, expand, or reinterpret contracts
- Later entries in history-log always supersede earlier ones for the same domain. Chronological order is the authority — the most recent entry wins.

Overwrite `/obelisk/contracts/contracts-summary.md`:
```markdown
# Contracts Summary

Generated: YYYY-MM-DD

[Concise list of active business invariants.]

## New
```

Contracts must be implementation-independent, durable across rebuilds, and free of code or UI detail.
Keep concise — under 1500 tokens. `## New` must remain present and empty after maintain.

---

Output:

✅ MAINTAIN COMPLETE
Contracts summary regenerated.