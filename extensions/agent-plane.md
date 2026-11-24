# Agent Plane

## What you get

Open the tmux sidebar to see which coding sessions are working, waiting for input or finished. Jump to a session or ask your agent to find it through the CLI. Agent Plane also lets you choose a background model. [precise//en](precise-en.md) uses that model to suggest words from your prompts.

## Requirements

macOS or Linux, tmux 3.3 or later, a supported coding agent, Rust and a C compiler.

## Installation

Choose the agents you run in tmux, where you want their status counts, and which keys should open the sidebar. Check those keys against your existing bindings before applying the configuration. Follow the project’s steps for the CLI, daemon, tmux plugin and agent skill. If you use precise//en, select its background agent in Agent Plane’s Configure menu. [Agent Plane installation](https://github.com/zazencodes/tmux-agent-plane#install)

## First task

With a coding agent open in tmux, ask it to find your sessions.

```text
List my coding agents in tmux and tell me which sessions are waiting for my input.
```

Open the Agent Plane sidebar and select a session from the list. You should land in the corresponding pane. The agent can get the same list with `tmux-agent-plane list`.

## Updating

Update the CLI and tmux plugin using their original installation methods, restart the daemon, and repeat the check.

## Uninstalling

Check whether precise//en is using the background agent. Remove the plugin entry, bindings, skill links and CLI installed during setup. Show edits to the user’s tmux and agent configuration first.
