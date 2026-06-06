# The Wiki — the town's shared records

This is the archive every teammate files into and reads from. The buildings are where teammates live and remember; the wiki is where the *work* is filed and found (full-text + vector search in the cloud).

On the dashboard this shows as the **records district**: each collection is an archive tile, distinct from the staffed buildings.

## Collections

The canonical set ships with the town (mirrors the backend in `collections.json`):

| Collection | Shape | Canonical file | What goes here |
|---|---|---|---|
| `owner` | flat-topic | — | Principal user: voice, rhythm, bio, values, expertise |
| `business` | flat-topic | — | The business this town serves |
| `team` | entity-as-folder | `profile.md` | Humans + agents on the team |
| `contacts` | entity-as-folder | `contact.md` | External people we interact with |
| `orgs` | entity-as-folder | `entity.md` | External organisations |
| `projects` | entity-as-folder | `project.md` | Active and historical projects |
| `decisions` | entity-as-folder | `decision.md` | Decisions made, with rationale |
| `knowledge` | entity-as-folder | `concept.md` | Curated knowledge concepts |
| `research` | dated-stream | — | Time-stamped investigations |
| `feedback` | dated-stream | — | User feedback, escalations, retros |
| `tasks` | entity-as-folder | `task.md` | Tasks, todos, in-flight work items |

## The three shapes

- **entity-as-folder** — `wiki/<collection>/<slug>/<canonical>.md` (+ optional attachments alongside)
- **dated-stream** — `wiki/<collection>/YYYY-MM-DD-<topic>.md`
- **flat-topic** — `wiki/<collection>/<topic>.md`

New collections are added deliberately (the Library tends the schema). Industry packs add their own collections on top.

Only `wiki/owner/` ships with content (skeleton templates the town fills on first conversation). Everything else starts empty.
