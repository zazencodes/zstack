# Changelog

All notable changes to zstack are documented here. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and versions follow [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Changed

- The README shows how the tools work together as an image, drawn with `diagram-viz`.

## [0.2.0] - 2026-11-26

### Added

- Added the [`diagram-viz`](https://github.com/zazencodes/skills/tree/main/skills/diagram-viz) skill to the catalog. It draws architecture diagrams, how-it-works pictures and timelines as images in the ZazenCodes style, and needs macOS, Google Chrome and the Inter and JetBrainsMono Nerd Font fonts.
- Added the [Motion Studio](extensions/motion-studio.md) extension. Your coding agent makes 3D system films and narrated explainers as code, reviews its own frames and audio, and hands you a finished 1920x1080 mp4. It needs macOS, Homebrew, Node.js 22 or later and uv.

## [0.1.0] - 2026-11-24

### Added

- Added the paste-in setup prompt. Your agent clones zstack to `~/.zstack/zstack` and links the `zstack` setup skill into `~/.agents/skills` and `~/.claude/skills`. Setup ends there if you choose no optional parts.
- Added the catalog (`catalog.toml`) of 12 skills from [zazencodes/skills](https://github.com/zazencodes/skills) and five extensions, with what each one needs.
- Added extension guides for Agent Plane, Snippets, Koyomi, precise//en and Swipe List. Each covers requirements, installation, a first task, updating and uninstalling.
- Added **configure zstack**, **update zstack** and **zstack status** requests for changing, updating and checking your stack after setup.
- Added the stack file, `zstack.toml`, which records your installed parts in your private skills repository.
- Added a diagram of how the extensions work together.
