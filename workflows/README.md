# workflows — the town's standing jobs

A **workflow** is a standing responsibility the town owns. You turn it on once; it fires on a trigger, does the work end to end, and reports back in a line. More than a recipe you run and more than a skill you have: it has a trigger that fires it, a goal it reasons toward, and ownership of an outcome over time.

Each lives at `workflows/<slug>/`:
- `recipe.yaml` — a standard Goose recipe. Its `instructions:` are the goal in plain language. Runnable on its own: `goose run --recipe workflows/<slug>/recipe.yaml`.
- `trigger.yaml` — when it fires + trust: `on:` (`inbox` | `schedule` | `webhook` | `demand`), `match:`/`cron:`, `trust:` (`auto` | `review` | `ask`), `owner:`, `status:` (`active` | `paused`).
- `log.md` — one-line receipts. `pending/` — drafts awaiting the owner's OK.

## The contract every workflow meets

1. **Closes a loop** — each run produces a moved outcome (filed, drafted, surfaced, nudged).
2. **Net-negative human work** — success is time given back, not a new to-do.
3. **Brief, silent when nothing moved** — no run, no noise.
4. **Trust-tiered** — never does something irreversible or outward without the owner's say.

## Trust tiers

- `auto` — reversible/internal (file, organise, recall): just do it.
- `review` — do the work, but anything outward or lossy (send email, publish, merge, delete) goes to `workflows/<slug>/pending/` as a draft; tell the owner it's ready.
- `ask` — confirm before acting.

## The starters that ship

| Workflow | Fires on | Trust | Status |
|---|---|---|---|
| **filing-cabinet** | a doc lands in `inbox/` | auto | active |
| **ask-my-cortex** | on demand | auto | active |
| **meeting-to-actions** | a recording lands in `inbox/` | review | active |
| **morning-brief** | daily 7am | auto | paused (turn on when ready) |
| **relationship-keeper** | weekly Mon 8am | review | paused |

Add one by asking an agent ("put my X on a workflow"). Pause one by setting `status: paused` in its `trigger.yaml`.
