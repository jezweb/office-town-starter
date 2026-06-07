# Templates

Blank skeletons for wiki records. Copy the matching file into the collection and fill it in:

| Copy | Into | As |
|---|---|---|
| `org.md` | `wiki/orgs/<slug>/` | `entity.md` |
| `contact.md` | `wiki/contacts/<slug>/` | `contact.md` |
| `project.md` | `wiki/projects/<slug>/` | `project.md` |
| `decision.md` | `wiki/decisions/<slug>/` | `decision.md` |
| `concept.md` | `wiki/knowledge/<slug>/` | `concept.md` |
| `task.md` | `wiki/tasks/<slug>/` | `task.md` |
| `profile.md` | `wiki/team/<slug>/` | `profile.md` |

Every record carries the universal sextet (`slug`, `kind`, `created`, `last_updated`, `last_edited_by`, `last_change_summary`) plus a `status`. See `wiki/AGENTS.md` for the shapes and the status vocabulary. These are reusable skeletons, the home for "a document about nothing in particular".
