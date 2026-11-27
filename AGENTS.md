# AGENTS.md

## Project Instructions

- Asked to set up, configure, update or check zstack for someone? Read `skills/zstack/SKILL.md` and follow it. The rest of this file is for changing the hub itself.
- Write `zstack`, all lowercase.
- Other repositories are read-only from here. Each skill and extension changes in its own repository.
- Do not commit, push or tag unless the user asks.

## Layout

- `README.md`: the page people land on, with the install prompt, the integration diagram and the extension and skill tables.
- `catalog.toml`: every skill and extension setup can offer. The zstack skill reads it.
- `skills/zstack/`: the setup skill, with `references/apply.md` and `references/stack-file.md`.
- `extensions/<id>.md`: one guide per extension.
- `docs/assets/tools.html` and `tools.png`: the integration diagram. Read `docs/diagram.md` before changing it.
- `.agents/`: local working notes, ignored by Git. `.agents/backlog.md` holds ideas, open questions and unfinished work Alex has raised. When he mentions something to look into later, add it there; when an item is done, delete it.

## Rules

- A part changes in three places together: its `catalog.toml` entry, its README row and, for an extension, its guide.
- A README skill row uses the catalog pitch. A README extension row links to the extension's repository.
- Adding or removing an extension, or changing how tools connect, may mean updating the integration diagram.
- An extension is `available` only when its repository is public and its install steps work for a stranger. Otherwise it is `unreleased`, and setup skips it.
- Every guide has six headings in this order: What you get, Requirements, Installation, First task, Updating, Uninstalling. It links to the extension’s own install instructions and keeps the detail there.
- Every file must stand alone on someone else’s computer: no private hostnames, account ids, email addresses, personal paths or real business records. Examples use fictional material.
- A change people will notice gets a line under `## [Unreleased]` in `CHANGELOG.md`.

## Validation

After changing the skill, a guide or the catalog, have a fresh agent run setup against a scratch home folder, then check the stack file it writes against `skills/zstack/references/stack-file.md`.
