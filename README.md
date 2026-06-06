# office-town-starter

The **whole default town** a new Office Town install starts from, and a self-contained one: the teammates, their skills, recipes, and hooks, plus the buildings, the wiki, and the collection manifest. It's content, not code. Clone or sync it, open Goose in it, and you have a working team. No separate plugin to install.

This replaces both the older `office-town` template and the `office-town-plugin` (its agents/skills/recipes/hooks are folded in here), and it's the single source the backend seeds new towns from.

## What's in here

```
AGENTS.md              town orientation + standing orders (Goose loads this at the root)
.agents/               the town's own Goose components (discovered because the town is the working dir)
  agents/              the 4 roles → @boss @librarian @worker @scout
  skills/              role techniques: build curate dispatch extract scan workflows
  recipes/             slash-command recipes (setup, weekly-sweep, triage-inbox, ...)
  plugins/office-town/ a project-scope plugin carrying just the session hooks
buildings/             the 4 home bases (a teammate + its memory), NOT the work
  office/    @boss      routes work, holds the thread
  library/   @librarian extracts + curates the wiki
  workshop/  @worker    deep work — builds, ships
  lookout/   @scout     scans outward (tools, industry, world)
wiki/                  the shared records (see wiki/AGENTS.md; only owner/ ships templates)
workflows/             standing jobs the town runs
collections.json       the default wiki collections — mirrors the backend's bootstrap
```

## How Goose finds all this (the town is self-contained)

Goose discovers components from the working directory, so with the town as your working dir it picks up everything here, no install step:

| Component | Where | Discovered as |
|---|---|---|
| Roles | `.agents/agents/*.md` | project agents → `@boss` etc. |
| Skills | `.agents/skills/*/SKILL.md` | project skills |
| Recipes | `.agents/recipes/*.yaml` | slash commands |
| Hooks | `.agents/plugins/office-town/hooks/hooks.json` | a project-scope plugin (enabled by default) |
| Orientation + standing orders | root `AGENTS.md` (+ per-folder `AGENTS.md`) | context hints |

Because it's all just files in the town, **the town owns its team** — you (or `@librarian`) can edit a brief, add a skill, or set up a new hook by writing files here, and they sync to every machine via the daemon. The agent can manage its own hooks the same way.

## The one thing wired separately: extensions

The 6 MCP **extensions** (`wiki`, `files`, `email`, `cron`, `voice`, `sandbox`) are not in this folder, they point at your Cloudflare backend ([`office-town-cloud`](https://github.com/jezweb/office-town-cloud)) and are wired into Goose once with `goose mcp add` (the backend's connect page generates the script). Everything *local* lives in the town; the *cloud services* are wired to the worker.

## The two layers

- **Buildings = home bases.** Where a teammate lives and remembers: `journal/`, `findings/`, `facts/`, `tasks/`, `inbox/` (plus `jobs/` for the Workshop, `instructions/` for the Library). A home base, not a fence — agents are induced and go wherever you point them, then come home to record.
- **Wiki = the shared archive.** Where work is filed and found; a project's wiki folder doubles as its workbench. Collections are in `collections.json` and mirror `office-town-cloud/src/bootstrap.ts`.

## No demo data, ever

A clean scaffold. Example/demo entries (sample contacts, fake jobs) never live here — they belong behind a `--with-examples` flag so they can't pollute a real town. Only `wiki/owner/` ships content (skeleton-with-prompts the town fills on first conversation).

## Related repos

| Repo | Role |
|---|---|
| [`office-town-cloud`](https://github.com/jezweb/office-town-cloud) | the Worker backend + 6 MCP extensions (code) |
| `officetowd` | local ⇄ R2 sync daemon (code) |
| **`office-town-starter`** | **this repo** — the whole self-contained town |
| ~~`office-town-plugin`~~ | retired — folded into this repo's `.agents/` |
| ~~`office-town`~~ | retired — the old template, replaced by this repo |

## License

MIT © Jezweb Pty Ltd. See [LICENSE](LICENSE).
