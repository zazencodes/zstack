# Snippets

## What you get

Save instructions you often give an agent, then insert them when composing a prompt. Each Markdown file in your snippets directory supplies one snippet. For example, save “Ask me which audience this is for before drafting” and select it when starting a new video brief.

## Requirements

macOS or Linux and at least one of Claude Code, Codex, Pi or OpenCode.

## Installation

Choose which agents should get snippets and whether to start with the supplied collection or an empty directory. Select `manage-snippets` if you want your agent to create and edit snippets for you. The installer sets up the selected agents and stores your collection in `~/.config/snippets`. [Snippets installation](https://github.com/zazencodes/snippets#install)

## First task

Insert a saved instruction into your next prompt. If you started with an empty collection and enabled `manage-snippets`, you can create your first one with this prompt.

```text
Save a snippet named “Audience first” that says “Ask me who the audience is before drafting.”
```

Open a fresh session and select your snippet. Use `/snippets` in Claude Code or Pi, `$snippets:` in Codex, or type `#` followed by the snippet name in OpenCode. If you picked “Audience first,” use it when you ask for a draft and check that the agent asks about the audience.

## Updating

Pull the installed checkout in `~/.local/share/snippets` and rerun setup for the same agents. After changing a snippet, use the upstream Codex sync step if Codex is among them.

## Uninstalling

Remove the per-agent entries created by the installer. Keep the user’s snippet collection unless they explicitly choose to delete it.
