# office-town-starter

The **default town** every new Office Town install starts from. It is content, not code: the buildings, the teammates' briefs, the empty wiki, and the collection manifest. Edit this and every new town changes, no deploy needed.

This is the single source for the default scaffold. It replaces the older `office-town` template and the hardcoded seeds in the backend.

## What's in here

```
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

- **Buildings = home bases.** Each is where a teammate lives and remembers: `journal/`, `findings/`, `facts/`, `tasks/`, `inbox/` (plus `jobs/` for the Workshop, `instructions/` for the Library). A building is a home base, not a fence — agents are induced and go wherever you point them, then come home to record. The role briefs ship in [`office-town-plugin`](https://github.com/jezweb/office-town-plugin); each one points its agent at the matching building here.
- **Wiki = the shared archive.** Where work is filed and found. A project's wiki folder doubles as its workbench. Collections are listed in `collections.json` and mirror `office-town-cloud/src/bootstrap.ts`.

## Where the teammates come from

The 4 role briefs are **not in this repo** — they ship in [`office-town-plugin`](https://github.com/jezweb/office-town-plugin) as an Open Plugin Spec plugin (`goose plugin install jezweb/office-town-plugin`), which Goose surfaces as `@boss`, `@librarian`, `@worker`, `@scout`. This repo provides the *places* those teammates work and remember (the buildings) and the records they file into (the wiki).

A town can add its own **per-town custom agents** in a local `.agents/agents/*.md` (Goose discovers project agents there when the town is your working directory). The universal 4 roles always come from the plugin, so they're never duplicated here.

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
