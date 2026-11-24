# The stack file

`zstack.toml`, at the root of the person’s skills repository, lists the parts zstack has installed for them. A part is listed once it is installed and taken off when it is removed. Nothing else goes in it.

The file is created when the user approves setting up optional parts. Linking the setup skill alone leaves this file absent. The agent keeps the file and commits every change to it. To change their stack, the person asks their agent to "configure zstack".

## Finding it

When `~/.agents/skills` links to the `agents` directory in the user’s skills repository, look for `zstack.toml` at that repository’s root. Resolve the symlink first, including relative links. On a new machine, verify both agent folders point into the intended repository before running setup.

## Example

```toml
# zstack.toml: the zstack parts installed for you.
# Your agent keeps this file. To change your stack, ask it to "configure zstack".

schema = 1

[zstack]
home = "~/.zstack"
commit = "4a004e9"
updated = "2026-11-19"

[you]
business = "Programming tutorials on YouTube, one online course, brand sponsorships. One person."
working_style = "Claude Code every day, usually two or three agents at once. Often away from the desk while they run."
wants = "Stop losing track of sponsor deals. Explain how my tools work in short videos."

[skills]
installed = ["init-agents-md", "git-commit-conventions", "adr", "tldr"]

[extensions]
installed = ["agent-plane", "snippets"]
```

## Fields

| Key | Meaning |
| --- | --- |
| `schema` | Always `1`. |
| `zstack.home` | Folder that holds zstack’s checkouts, written with `~`. The core checkout is `<home>/zstack`; any other repository zstack clones goes in `<home>/<repository name>`. |
| `zstack.commit` | Short commit of the core checkout at the last apply. Update compares the catalog against it to find what is new or newly released. |
| `zstack.updated` | Date of the last apply, `YYYY-MM-DD`. |
| `you.business` | What the business does, in their words. Used to recommend parts. |
| `you.working_style` | How they work with their agent, in their words. Used to recommend parts. |
| `you.wants` | What they want off their plate, in their words, including wants no part meets yet. Used to recommend parts now and when new ones are released. |
| `skills.installed` | Ids of the catalog skills copied into the skills repository. A skill that comes with an extension belongs to that extension and is not listed. |
| `extensions.installed` | Ids of the extensions whose install finished and whose **First task** outcome was verified. Only `available` extensions can be here. |

Ids must exist in `<core>/catalog.toml`. Report unfamiliar ids and preserve them until the user decides what to do.
