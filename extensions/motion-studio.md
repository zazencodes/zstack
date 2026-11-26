# Motion Studio

## What you get

Your coding agent makes short films as code. A 3D system film shows a system you describe, or a repository you point at, under a dark terminal HUD with a score on the beat. A narrated explainer covers a news event or an article, with subtitles. The agent renders each film, reviews its own frames and measures its audio before it shows you the finished 1920x1080 mp4. Narration uses Kokoro, a free voice that runs on your Mac.

## Requirements

macOS with Homebrew, Node.js 22 or later and uv. Set up downloads about 1.2 GB and uses about 2.2 GB of disk, counting the browser and package caches. ElevenLabs narration is optional and needs your own API key.

## Installation

Clone the studio to `~/motion-studio`, or to a folder the owner names. Their films are saved in its `projects/` folder, which git ignores, so back that folder up the way you back up your other work. Follow its Set up section. Set up is complete when `tools/check-setup.sh` ends with `Set up is complete.` [Motion Studio set up](https://github.com/zazencodes/motion-studio#set-up)

## First task

Open your coding agent in the studio folder and render the example film.

```text
Render the print queue example.
```

The agent opens the finished film when it has checked it. Then describe a system you know and ask for a 3D system film of it.

## Updating

Follow the upstream Update section. It leaves the films in `projects/` as they are.

## Uninstalling

Ask the owner which films in `projects/` to keep before removing anything. The upstream Remove section covers the studio folder and what set up installed outside it.
