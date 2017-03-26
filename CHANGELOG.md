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
