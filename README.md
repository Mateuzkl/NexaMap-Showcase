# NexaMap Editor — Community Update Showcase

[![Live Showcase](https://img.shields.io/badge/Live_Showcase-Open-19d3e5?style=for-the-badge)](https://mateuzkl.github.io/NexaMap-Showcase/)
[![NexaMap Editor](https://img.shields.io/badge/Source-NexaMap_Editor-7c4dff?style=for-the-badge)](https://github.com/Mateuzkl/NexaMap-Editor)
[![Pull Request](https://img.shields.io/badge/Update-PR_%2331-40df91?style=for-the-badge)](https://github.com/Mateuzkl/NexaMap-Editor/pull/31)

This repository hosts the public showcase for a major NexaMap Editor update. The full visual presentation is available at:

## [Open the live NexaMap Showcase](https://mateuzkl.github.io/NexaMap-Showcase/)

Development is tracked in [NexaMap Editor pull request #31](https://github.com/Mateuzkl/NexaMap-Editor/pull/31). The editor source code, releases, issues, and contributions belong in the [original NexaMap Editor repository](https://github.com/Mateuzkl/NexaMap-Editor).

## Changelog

### Workspace and resource discovery

- Rebuilt the startup experience around a compact Client + Server Workspace.
- Added automatic discovery for maps, `items.otb`, `items.xml`, `appearances.dat`, monsters, and NPCs.
- Added support for Classic TFS, Canary, and Crystal resource layouts.
- Added persistent workspace state, bounded scanning, file fingerprints, and clearer validation errors.
- The configured primary world map can be opened directly from the workspace.

### Independent map sessions

- Added independent resource sessions for map tabs.
- Each tab can use a different client, server, item database, protocol, and map.
- Switching tabs restores the complete resource state without reloading or affecting other open maps.
- Multiple views can safely share one editor while preserving deterministic ownership and cleanup.

### Cross-client copy and paste

- Added a transfer clipboard for copying map areas between different clients.
- Added item matching based on metadata, structure, graphics, and visual fingerprints.
- Added a review flow for matched, remapped, and missing items before applying a paste.
- Added manual destination mapping with search, previews, categories, and tilesets.
- Large pastes remain undoable and are applied in bounded chunks.
- Closed source sessions are no longer retained by clipboard content.
- RGBA previews now have per-preview and total memory limits.

### Editing and navigation tools

- Added a Quick Command Palette for faster access to editor actions.
- Added Favorites 2.0 with persistent, categorized, session-aware entries and previews.
- Added a dockable minimap with viewport navigation and Action ID / Unique ID markers.
- Added Map Diagnostics with filtering, progress, cancellation, and direct navigation to issues.
- Added improved item tooltips and visual container previews.
- Added space-drag panning and improved Find Item interactions.
- Collections palettes now follow the active resource session and stay hidden when unavailable.

### Local playtest

- Replaced the older in-game preview with a richer local Playtest mode.
- Added movement, interaction, HUD, lighting, weather, camera handling, and keyboard controls.
- Improved teardown when closing Playtest, switching sessions, or closing map tabs.

### Multiplayer editing

- Added Host and Join sessions with authentication and asset compatibility checks.
- Added map snapshots, revision tracking, transactions, permissions, locks, chat, cursors, pings, reconnect, and resynchronization.
- Hardened session shutdown, rejection paths, partial snapshots, DNS failures, and slow connection handling.

### Renderer and performance foundations

- Added 4×4 chunk revision tracking and targeted invalidation.
- Added CPU geometry caching and persistent GPU ground caching.
- Added atlas epoch tracking and FBO scene cache integration.
- Preserved exact rendered output while reducing warm ground-stream uploads in the measured synthetic scene.
- Hardened GPU cache budget arithmetic and OpenGL resource teardown.

### Lifetime and reliability improvements

- Replaced manual MapTab reference counting with explicit shared state.
- Changed single-owner objects to `std::unique_ptr` or value members where appropriate.
- Replaced detached editor deletion with an application-owned, joinable disposal queue.
- Protected deferred wxWidgets callbacks with weak references and runtime revalidation.
- Made frame teardown idempotent to prevent duplicate OpenGL end-frame work.
- Reset diagnostics state fully and cancel scans after map, session, or revision changes.
- Removed duplicated popup guards and other superseded manual cleanup paths.
- Fixed duplicate helper definitions that previously broke CMake unity builds.

## Validation

- Full Windows Release x64 unity build completed successfully.
- All 35 local unit and integration tests passed.
- clang-format 16 passed for every source file selected by the CI workflow.
- AddressSanitizer passed the native lifecycle, OpenGL, and multiplayer validation scenarios.
- OpenGL cache tests produced exact cache ON/OFF pixel equivalence on Intel UHD Graphics.
- GitHub Actions continues to validate Windows x86 and x64 builds for the active pull request.

## Feedback and contributions

Community testing is welcome. Real maps, different client versions, and different server distributions help uncover compatibility and workflow issues that automated tests cannot reproduce.

- Report bugs or request improvements in [NexaMap Editor Issues](https://github.com/Mateuzkl/NexaMap-Editor/issues).
- Review and test the current work in [pull request #31](https://github.com/Mateuzkl/NexaMap-Editor/pull/31).
- Fork the [original NexaMap Editor repository](https://github.com/Mateuzkl/NexaMap-Editor), create a focused branch, and open a pull request with a clear description and validation results.
- Include reproduction steps, client/server versions, relevant logs, screenshots, and a small test map when reporting a problem.

Please submit editor fixes and features to **NexaMap Editor**. This showcase repository contains only the static community update page.

## Project links

- [Live showcase](https://mateuzkl.github.io/NexaMap-Showcase/)
- [NexaMap Editor source](https://github.com/Mateuzkl/NexaMap-Editor)
- [Current update pull request](https://github.com/Mateuzkl/NexaMap-Editor/pull/31)
- [Issues and feedback](https://github.com/Mateuzkl/NexaMap-Editor/issues)
