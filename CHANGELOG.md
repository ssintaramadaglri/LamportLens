# Changelog

All notable changes to LamportLens are documented in this file.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Nothing yet. This section collects the next change.

## [2.1.0] - 2026-08-26

### Added

- The audit text report closes with a totals summary line: records,
  total bond, underfunded deficit, and the lamports a closure sweep
  would return.
- The `bands` report prints the executable-excluded count next to the
  seven fixed bands, so the excluded accounts are never silently lost.

### Fixed

- Owners table ordering is stable when two owners hold equal locked
  lamports (address order breaks ties instead of insertion order).

## [2.0.0] - 2026-08-05

### Changed

- The JSON report moves to fixed snake_case field names (`bands`,
  `owners`, `totals`, `parse_errors`) so downstream dashboards can
  pin a schema. This is the one breaking change in the 2.x line.
- The text report header line and column layout are frozen; the
  `LAMPORTLENS REPORT` banner only changes with a major version.

## [1.5.0] - 2026-07-14

### Added

- `audit --limit N` caps the number of listed findings while the
  totals still cover the whole snapshot.
- `lamportlens version` as a subcommand, alongside the existing
  `--version` flag.

### Documentation

- `docs/TESTING.md` collects the local test recipe for both engines.

## [1.0.2] - 2026-06-02
