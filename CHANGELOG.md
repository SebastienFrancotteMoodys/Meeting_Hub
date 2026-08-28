# Changelog

All notable changes to Meeting Hub are documented here.
Versioning: `vMAJOR.MINOR.PATCH` — a new feature bumps MINOR, a fix bumps PATCH.

## v0.2.0 — 2026-08-28
### Added
- **Note → Action**: turn any note line into a prefilled, bidirectionally-linked action (owner auto-detected).
- **Prep carry-over**: prep cards show open actions + open questions from the last meeting of the same base subject; actions are clickable and jump to the board.
- **Local-folder storage** (File System Access API): auto-save to `meeting-hub.json` in the connected folder, with fallback to `localStorage`.
- **Auto-import inbox**: the app watches `meeting-hub-inbox.json` and imports meetings dropped there — no copy-paste.
- **Screenshots in notes**: paste / drop / pick, downscaled and stored in `images/`, viewable in a lightbox.
- **In-app version indicator** in the ⋯ menu.
### Changed
- **Prep matching** now uses the *base subject* (everything before the first `-`), case/space-insensitive — e.g. prep "Hadoop migration" matches "Hadoop migration - PM design".

## v0.1 — initial
- Kanban actions + notes hub (baseline).
