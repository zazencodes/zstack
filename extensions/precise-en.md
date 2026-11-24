# precise//en

## What you get

A prompt hook looks for a phrase you could replace with one precise word. For example, “safe to run twice with the same result” might yield *idempotent*. The hook passes qualifying prompts to the background model selected in [Agent Plane](agent-plane.md). Saved suggestions go to your Cloudflare database for review on Mac or iPhone.

## Requirements

Claude Code or Codex on a Mac, macOS 15 or later, Xcode, xcodegen, Apple signing, a Cloudflare account and Node.js 22. Agent Plane must have a working background agent. Prompts of 50 words or more are sent to its model.

## Installation

Set up Agent Plane and choose the background model that will receive qualifying prompts. Decide whether Claude Code, Codex or both should have the hook. Follow the project’s steps for the Cloudflare Worker and database, local configuration, Mac app and CLI. Add the iPhone client if you want to review words there too. [precise//en setup](https://github.com/zazencodes/precise-en#setup)

## First task

Try this prompt in a session with the hook enabled.

```text
Help me explain to a teammate why a payment button should be safe to press twice. Someone on a slow connection might click it again because the first click looks like it did nothing. Give me one short paragraph for the team and a concrete example of what the customer would see on their receipt.
```

Check the capture log for the prompt. If the background agent suggests a word, open the Mac app to review it alongside your original phrase.

## Updating

Follow the project’s deployment and build steps for the Worker and installed clients. Recheck the hook after updating the CLI.

## Uninstalling

Disable the prompt hook, quit the app and remove the installed clients and CLI. Ask before deleting the Cloudflare Worker or the database holding the user’s words.
