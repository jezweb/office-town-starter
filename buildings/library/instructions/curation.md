# Curation playbook

How the Library keeps the wiki clean and scoped. These are **defaults to start from, not laws** — tune them to the owner's rhythm. The point is that "current" becomes a decision the librarian makes on a rule, not a vibe.

## The pass (weekly, or on demand)

1. **Merge duplicates.** Two records for the same entity → keep the canonical slug, merge the content in, repoint any links, leave a one-line note in the dropped one before removing it.
2. **Re-file state.** Set `status` so the active records aren't crowded by dead ones (see thresholds below). Never delete (records are graph nodes; deleting orphans links) — mark state instead.
3. **Cross-link.** Connect a record to the contact/decision/project it relates to.
4. **Graduate findings.** A finding that's appeared 3+ times and is portable → `wiki/knowledge/<topic>/concept.md`.

**Done when:** every collection scanned, duplicates merged, stale entries marked, and today's journal has a one-line note of what changed and what got proposed for archive.

## Staleness thresholds (starting defaults)

| Record | Propose this status when... |
|---|---|
| `contacts` | no edit AND no inbound link from a project/decision in **~12 months** → `dormant`; explicitly gone (left, dead) → `former` |
| `orgs` | no active project or contact AND untouched **~12 months** → `dormant`; relationship ended → `former` |
| `projects` | finished → `done`; dropped/stalled with no intent to resume → `abandoned`; `active` with no `last_updated` movement in **~30 days** → flag as stalled (surface to owner, don't auto-change) |
| `decisions` | replaced by a newer decision → `superseded` (link to the replacement) |
| `knowledge` | replaced → `superseded`; contradicted or out of date → `stale` |

`last_updated` means "last touched", not "last verified" — don't rely on it alone; the `status` field is the real signal.

## Archiving is lossy → propose, don't auto-do

Marking `status` is safe and reversible, so do it directly. But anything that *removes* a record from view (an actual archive/delete) is lossy: propose it to the owner via a workflow's `pending/` tray rather than doing it silently. The owner can always say "yes, clear those out."

## Don't over-prune

The cost of keeping a quiet record is low; the cost of losing one (and its links) is high. When in doubt, mark `dormant` and leave it. Dormant is recoverable; deleted is not.
