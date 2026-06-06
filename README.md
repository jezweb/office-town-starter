# office-town-starter

The **default town** every new Office Town install starts from. It is content, not code: the buildings, the teammates' briefs, the empty wiki, and the collection manifest. Edit this and every new town changes, no deploy needed.

This is the single source for the default scaffold. It replaces the older `office-town` template and the hardcoded seeds in the backend.

## What's in here

```
.agents/agents/        the 4 teammate briefs — Goose discovers these as @boss/@librarian/@worker/@scout
buildings/             the 4 home bases (a teammate + its memory), NOT the work
  office/    @boss      your primary contact; routes work, holds the thread
  library/   @librarian extracts + curates the wiki
  workshop/  @worker    deep work — builds, ships
  lookout/   @scout     scans outward (tools, industry, world)
wiki/                  the shared records (only owner/ ships with templates; rest empty)
workflows/            standing jobs (none ship; add your own or install a pack)
collections.json      the default wiki collections — mirrors the backend's bootstrap
```

## The two layers

- **Buildings = home bases.** Each is where a teammate lives and remembers: `journal/`, `findings/`, `facts/`, `tasks/`, `inbox/` (plus `jobs/` for the Workshop, `instructions/` for the Library). A building is a home base, not a fence — agents are induced and go wherever you point them, then come home to record. The brief in `.agents/agents/<role>.md` points each agent at its building.
- **Wiki = the shared archive.** Where work is filed and found. A project's wiki folder doubles as its workbench. Collections are listed in `collections.json` and mirror `office-town-cloud/src/bootstrap.ts`.

## How Goose finds the teammates

Goose discovers agents from flat `.agents/agents/*.md` files (with YAML frontmatter), so the briefs live there and become `@boss`, `@librarian`, `@worker`, `@scout` when you open Goose with the town as your working directory. The building folders hold each teammate's memory; the brief body points the agent home.

## No demo data, ever

This starter is a clean scaffold. Example/demo entries (sample contacts, fake jobs) never live here — they belong behind a `--with-examples` flag so they can't pollute a real town.

## Related repos

| Repo | Role |
|---|---|
| [`office-town-cloud`](https://github.com/jezweb/office-town-cloud) | the Worker backend + MCP gateways (code) |
| `officetowd` | local ⇄ R2 sync daemon (code) |
| `office-town-plugin` | the teammates' skills, recipes, hooks, and tests (Goose side) |
| **`office-town-starter`** | **this repo** — the default town content |

## License

MIT © Jezweb Pty Ltd. See [LICENSE](LICENSE).
