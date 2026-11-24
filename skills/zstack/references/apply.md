# Apply

Use Apply only for approved changes to optional parts. When the person chose no optional parts, finish after linking the setup skill as described in [the zstack skill](../SKILL.md).

Apply makes the machine match the stack the person agreed to: the parts in their stack file, plus the ones they just chose, minus the ones they just removed. It is safe to run again: each step checks before it changes anything. Work through the steps in order and write each part to the stack file as you finish it.

Some steps need the person: signing in, pairing a device, creating an account. Tell them exactly what to do and wait for them. For a command that prompts (a login, a pairing code), ask them to run it in their own terminal and tell you when it is done.

When a need is missing (`uv`, `ffmpeg`, `tmux` and the like), name it and ask whether to install it. With their yes, install it with the system’s package manager (Homebrew on macOS, the distribution’s own on Linux) or the tool’s official installer. With a no, leave that part out and go on.

`<core>` is the zstack checkout and `<home>` is its parent. `<skills>` is the user’s skills repository. Its **skill folders** are `<skills>/agents`, which `~/.agents/skills` links to, and `<skills>/claude`, which `~/.claude/skills` links to. Every skill zstack adds goes in both. The repository’s `AGENTS.md` asks which folders a new skill goes in; the plan they agreed to has answered that. To **link** a skill is to make a symbolic link named after it in both skill folders, pointing at the skill folder. Use a relative link from the real destination directory so the same layout works under a different home.

## 1. The skills repository

When `~/.agents/skills` and `~/.claude/skills` are links to the `agents` and `claude` folders of one git repository, that is their skills repository. Go to step 2.

When only one of them is, or either links somewhere else, tell them what you found and stop. Set up nothing until they decide what to do with it.

For a new skills repo, first confirm the Python interpreter used for the template is 3.10 or later. If it is missing, resolve that with the user before moving any links. Use the GitHub name and folder from the approved plan:

1. `gh repo create <name> --private --template zazencodes/agent-skills`, then `gh repo clone <owner>/<name> <folder>`. When the plan said to use a repository they already had, only clone it.
2. Before migrating the two agent folders, temporarily unlink the verified zstack skill symlinks in them. The template copies directory contents and could otherwise import the linked skill as ordinary files. At every exit from the migration, including an error or a cancelled dry run, restore those links in the current skill folders following [Link the setup skill](../SKILL.md#link-the-setup-skill). Preserve any conflicting entry and report it.
3. In `<folder>`, run `python3 setup_symlinks.py --dry-run --agents=agents,claude`. It plans to move what is in `~/.agents/skills` and `~/.claude/skills` into the repository, keep a backup under `.agent-skills-setup/backup/`, and link both folders back to it. When its plan differs from what you told them, or it refuses a state it cannot handle, tell them what it said and stop.
4. Run it for real, answering its confirmations: `yes | python3 setup_symlinks.py --agents=agents,claude`.
5. Look through the skills it moved in for credentials: keys, tokens, passwords. Point out any you find, and let them decide what to do with each before you commit. The backup is never committed; tell them it still holds anything they take out.
6. Commit the moved-in skills with the message "Import my existing skills" and push. Skip this when nothing moved in.

**Verify:** `~/.agents/skills` and `~/.claude/skills` resolve to `<skills>/agents` and `<skills>/claude`.

## 2. The zstack skill and the stack file

Link `<core>/skills/zstack` under the name `zstack` in both skill folders. Reuse matching links. If a destination contains a different skill, show it and ask before replacing it. From then on they can ask for zstack in any session.

When `<skills>/zstack.toml` does not exist yet, write it as [the stack file reference](stack-file.md) defines, with `zstack`, `you` and empty `installed` lists. `zstack.home` is the parent of `<core>`, written with `~`. Step 5 brings `zstack.commit` and `zstack.updated` up to date.

## 3. Skills

For each catalog skill they chose, read its entry. Reuse intact installed copies. If an installed copy is missing, verify the other copy and repair the missing one without overwriting edits.

1. The source checkout is `<home>/<repository name>`, where the name is the part of `repo` after the slash. Clone `https://github.com/<repo>` there if it is missing.
2. Check the skill’s `needs`. When one is missing, say which and ask whether to install the need or leave the skill out.
3. When either skill folder already has an entry named `<id>` that differs from `<source checkout>/<path>`, stop for that skill, say what is there and ask whether to replace it. Never overwrite it unasked.
4. Copy `<source checkout>/<path>` into both skill folders as `<id>`, and add the id to `skills.installed`.

For a skill they removed, delete `<id>` from both skill folders and take it out of `skills.installed`. Git history keeps it.

**Verify:** both skill folders hold `<id>/SKILL.md` for every id in `skills.installed`.

## 4. Extensions

Install the selected entries marked `available` in the catalog. Apply prerequisites first. For entries already recorded, verify the existing install and offer to repair it if its check fails. For each new extension:

1. Read the guide. Confirm its **Requirements** and the catalog’s required extensions are installed and working. If a prerequisite fails its check, skip the dependent extension. A missing tool follows the rule at the top of this file. An account or sign-in that installation creates is theirs to do during the install. When they cannot supply something now (a credential file they do not have, a required extension that is not installed), leave the extension out, tell them what would let it install and go to the next one.
2. Read **Installation** and settle the setup choices the user has not already made. Use the guide’s documented default when they choose it. If an unanswered question affects setup, wait for their answer.
3. Follow **Installation**. Where it points to the extension’s own instructions, read those and follow them in order. Read an install script before running it and tell them what it will change. Show changes to the person’s files before making them.
4. Use **First task** to confirm the installation works. Ask the user to perform any steps that require their phone, app or interactive session. Add the id to `extensions.installed` after confirming the stated result. If verification fails or is pending, leave the id out and report why.

For an extension they removed, describe what its guide’s **Uninstalling** section will do, ask, then do it and take the id out of `extensions.installed`.

## 5. Record

1. Set `zstack.commit` to `git -C <core> rev-parse --short HEAD` and `zstack.updated` to today.
2. Commit `zstack.toml`, the `zstack` skill links and the skills zstack added, replaced or removed in this run, including links an extension’s installer made, with a message that says what changed in their stack. Leave any other changes in the repository alone. Push.
3. Report what was installed, what was left out and what would let it install, and anything they still need to do themselves.
