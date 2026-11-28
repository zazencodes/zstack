---
name: zstack
description: Use only when the user explicitly names zstack and asks to set it up, configure it, update it, check its status, or remove its skill links.
---

# zstack

Help the person choose and install the parts of Alex’s business stack that fit their work. Resolve the real path of the directory containing this SKILL.md. The checkout three directories above that directory holds `catalog.toml` and the extension guides. Use those files for the versions and dependencies this checkout supports.

## Link the setup skill

On an explicit setup request, make the setup skill available for this user before offering other parts. The checkout is the one containing this file.

1. Inspect both destinations, `~/.agents/skills/zstack` and `~/.claude/skills/zstack`. Follow valid parent-directory links. Reuse an existing symlink that resolves to this checkout’s `.agents/skills/zstack` directory. If a destination is occupied by anything else or a parent link is broken, show the conflict and pause before changing either destination.
2. Create any missing parent directories and link the two names to the skill directory. Use a relative target from each destination’s resolved parent. Verify that reading SKILL.md through each link opens this file. On a partial failure, undo links created by this attempt and report the failure.
3. Report which links you created or found, their paths, and the checkout they point to. If a link landed inside a git repository, say that it shows there as an uncommitted change. Tell the user they can ask to remove the zstack skill links. Offer to walk through the optional parts or stop here. Wait for their choice unless they already gave it.

On a request to remove the zstack skill links, inspect both destinations. Unlink just the symlinks that resolve to this checkout’s skill, keeping the target and other entries intact. Report exactly what you removed. If the links are tracked in their skills repo, mention the local change. Status, update and removal do not run first-time setup.

## Choose parts

1. Ask what the person’s business does, what they want help with and how they use their agents. Reuse anything they have told you. Show a one-screen menu of the catalog’s skills and its extensions marked `available`. Keep the menu within 24 rows at 80 columns. List the four starter IDs together, group the other skill IDs by purpose, and give each extension one short line. Offer details on request. Let them choose any combination, including none. A recommendation counts as a selection only when the user accepts it.
2. If they decline everything on first setup, say that only the setup skill is linked and finish. On a later configure request with no changes, report that nothing was added or removed. This path ends before checking GitHub sign-in, creating a skills repo, moving skills, writing a stack file, installing dependencies, committing or pushing. On a later configure request, preserve any previously installed parts unless they explicitly ask to remove them.
3. For selected extensions, read their guides and check requirements. Offer any missing dependency with the reason it is needed. If they ask for an extension that is `unreleased` or whose repository cannot be reached, skip it, say why, and drop dependencies needed only by a skipped part. If no installable selections remain, explain why and stop here.
4. Identify the existing skills repo from the linked agent folders, or propose a private GitHub repo from the template, cloned to `~/agent-skills`. Check Git authorship and, if creating or cloning a repo, GitHub CLI access. Present the skills repo, any existing skills that will move, backups, selected parts and dependencies together in one plan. Proceed only after the user approves it. If they decline, stop with their existing setup.
5. Follow [Apply](references/apply.md). Save their answers under `you` in the [stack file](references/stack-file.md). Record each part after its checks pass, then report what they can try.

## Configure, update or check

- **Configure zstack.** Read the catalog and the stack file if present. If only the setup skill is linked, begin at Choose parts. For additions, confirm choices and apply the approved plan. For removals, show what the guide will remove and confirm first. Check for installed dependents before removing their prerequisite.
- **Update zstack.** With only the setup skill installed, fast-forward its checkout and stop. Otherwise compare the installed skill copies with their source checkout before pulling. Fast-forward the hub and source checkouts, preserving local changes. Offer new catalog parts, update unmodified skills, and show upstream changes before merging or replacing a user-edited copy. Follow the local guide’s Updating section for each installed extension and record successful changes with Apply.
- **zstack status.** Inspect the skill links. If there is no stack file, report which links are present and that no optional parts are recorded, then stop. Otherwise verify both copies of each installed catalog skill, and each installed extension’s current state using the outcome described under First task. Use existing results or a read-only check during status. Report what needs attention and any uncommitted or unpushed changes in the user’s skills repo.
