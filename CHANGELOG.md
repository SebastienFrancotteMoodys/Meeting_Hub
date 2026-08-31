# Changelog

All notable changes to Meeting Hub are documented here.
Versioning: `vMAJOR.MINOR.PATCH` — a new feature bumps MINOR, a fix bumps PATCH.

## v1.0.0 — 2026-08-31
### Changed
- **First stable release.** No functional change over v0.8.0 — this marks the meeting loop as complete: capture → `/close-meeting` → auto-import from `meeting-hub-inbox.json` → `/enrich-meeting` to fold in a second source, on top of actions, notes, preps with carry-over, focus, screenshots and auto-archiving.

> Housekeeping: two out-of-sequence tags (`v1.0` on an early screenshots commit, `v0.1` on a README edit) were deleted with this release. Their commits remain in `main`; only the tag names are gone. Every release is tagged `vMAJOR.MINOR.PATCH`.

## v0.8.0 — 2026-08-31
### Added
- **Enrich an existing note** — an import payload carrying `"mode": "enrich"` now updates a note that is already on the board instead of creating a second one. Made for folding in notes from another source (a Copilot transcript, a colleague's minutes, a recap email) after the meeting was already closed. The note's bullets are replaced by the reconciled set, participants are merged, and the toast offers **Undo**.
- Enrich targets a note by exact title + date, then falls back to the base subject (everything before the first `-`) + date, then the title alone. `prep` notes are never targeted, and when nothing matches the payload is imported as a new note with a notice.

### Changed
- Actions in an enrich payload go through the usual dedupe (`summary` + `meeting`), so re-sending known actions is a no-op while genuinely new ones are added.

## v0.7.0 — 2026-08-28
### Changed
- **Focus toggle moved next to the search bar** — a ★ button with a live count of focused actions, replacing the status-strip chip. Disabled when nothing is focused.
- **Tighter header**: the status strip now collapses when empty, reducing the gap between the toolbar and the board.

## v0.6.0 — 2026-08-28
### Added
- **Auto-archive Done**: an action that has sat in Done for 24h leaves the board automatically. It is kept in the data file and can be restored from ⋯ → "Archived actions" (Restore back to Done, or Delete). Existing Done cards get a fresh 24h grace on first load — nothing is purged on upgrade.

## v0.5.0 — 2026-08-28
### Changed
- **Status strip decluttered**: removed the open / overdue / to-confirm counters. The strip now shows only the Focus chip and the active-search indicator.

## v0.4.0 — 2026-08-28
### Added
- **Focus selection**: star any action to add it to your personal Focus list, and a **focus** chip in the status strip to show only your starred actions across all columns. Persistent (managed by hand).

## v0.3.0 — 2026-08-28
### Changed
- **Kanban toolbar streamlined.** Removed "Paste from Claude" (superseded by the auto-import inbox) and the download button (backup now lives in the ⋯ menu).
- **New items are now three dedicated toolbar icons**: New action, New note, New prep.
- Refreshed empty-state guidance to the `capture` → `/close-meeting` → auto-import flow.

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
