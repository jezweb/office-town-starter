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
| `tasks` | entity-as-folder | `task.md` | **Shared, owner-visible** work that crosses roles or outlives a session |

A note on `tasks`: the wiki `tasks` collection is for work the **owner should see** or that **crosses roles** ("what's outstanding?"). An agent's own private, single-session worklist stays in its building's `tasks/` folder. Personal worklist in the building; shared work in the wiki.

## The three shapes

- **entity-as-folder** — `wiki/<collection>/<slug>/<canonical>.md` (+ optional attachments alongside)
- **dated-stream** — `wiki/<collection>/YYYY-MM-DD-<topic>.md`
- **flat-topic** — `wiki/<collection>/<topic>/` (a folder per topic; the main file is `<topic>.md`, documents and notes sit beside it)

`owner` and `business` are flat-topic but still **folders, not loose files**: `wiki/owner/voice.md`, `wiki/business/<business-name>.md`. That gives a document about the owner's own business somewhere to sit (e.g. a budget at `wiki/business/fy26-budget.xlsx`).

## Where documents go

A document you *produce* (a letter, budget, deck, report, image) lives **beside the record it's about**:

- about an external org → `wiki/orgs/<slug>/offer-letter.docx`
- about a contact → `wiki/contacts/<slug>/<doc>`
- about the owner's own business → `wiki/business/<doc>`
- about nothing in particular → a blank skeleton is in `templates/`; a genuinely standalone reference goes in `knowledge/`

The record is the markdown entry; the document is an attachment beside it. Never `/tmp`, never a loose top-level folder.

## Status and retention (the brake)

Entity records carry a `status` so the town stays scoped to current work instead of growing into an archive of everything:

- contacts / orgs: `active | dormant | former`
- projects: `active | done | abandoned`
- decisions: `active | superseded`
- knowledge: `active | superseded | stale`

Nothing is deleted (records are graph nodes; deleting one orphans its links). State is re-filed instead: a finished project becomes `done`, a long-quiet contact becomes `dormant`. `last_updated` means "last touched", not "last verified" — `status` is what tells you, the librarian, and the operator what's still alive.

## Who writes what

- **@librarian** owns extraction and curation: `orgs`, `contacts`, `team`, `knowledge`, and the schema. New entities from email / files / briefs come in through the Library.
- **@worker** writes the records for the work it produces: `projects/` and `decisions/`. If a build surfaces a new org or contact, it files a finding and hands the entity to the Library rather than creating it itself.
- **@operator** updates `status` and follow-up state on existing records as loops move; it doesn't create new entities.
- **@boss** / **@scout** file observations into their building `findings/`; the Library graduates the durable ones.

New collections are added deliberately (the Library tends the schema). Industry packs add their own collections on top.

Only `wiki/owner/` ships with content (skeleton templates the town fills on first conversation). Everything else starts empty.
