# Swipe List

## What you get

Save a screenshot or link from your phone or Mac, with a note about the detail you want to remember. [Koyomi](koyomi.md) runs a worker on your Mac that collects the media, describes it and tags it. When you next work on a thumbnail or a page, ask your coding agent to find references in your library. The server supplies the `swipe` CLI and its own `inspo-swipe-list` skill.

## Requirements

A Linux server, domain, Neon project and Tailscale for the phone dashboard. You deploy from a Mac or Linux computer with Node.js 24 or later. The worker needs a Mac with Koyomi, Codex, its Chrome integration, Chrome, FFmpeg and Node.js 24 or later. The optional native Mac client requires macOS 15 or later and Xcode Command Line Tools.

## Installation

Choose a server for your library and a dedicated macOS user and Chrome profile for the scheduled worker. The worker can access that account’s files and browser sessions. Decide where you want to save references and which coding agents should be able to search them. The project’s self-hosting guide covers the server, phone dashboard, Koyomi job and native Mac app. The server supplies the CLI and agent skill for your library. [Swipe List self-hosting guide](https://github.com/zazencodes/swipe-list/blob/main/docs/self-hosting.md)

## First task

Save a design reference from your phone and give it a distinctive note, such as “cover lettering for the autumn issue.” Once the worker processes it, ask your agent to find it.

```text
Search my Swipe List for the reference I saved about cover lettering for the autumn issue. Show me the matching item and my note.
```

Compare the result with what you saved, in the phone dashboard or the Mac app. If it hasn’t appeared, `swipe whoami` shows your credential and dashboard address, `koyomi show swipe-list-worker` shows the last scheduled run, and `swipe search --status done` lists processed items.

## Updating

Follow the upstream Update section for the server, worker, CLI, skill and Mac app. Repeat the saved-reference check.

## Uninstalling

Stop the scheduled job before taking down the worker and server. The upstream Remove section covers each client and service. Ask the owner what to retain before removing uploaded media or the library database.
