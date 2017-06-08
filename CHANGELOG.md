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

### Fixed

- Records whose data length sits exactly on a band edge now land in
  the same band in both engines; the boundary rule is pinned by a
  regression test and by the parity gate.
- The parse-error count is reported in the JSON report even when no
  findings are present.

## [1.0.0] - 2026-05-19

### Changed

- The CLI contract is stable: `audit`, `bands` and `owners`, the flag
  set, and the exit codes (0 clean, 1 findings or parse errors, 2
  usage) are frozen for the 1.x line.
- Reports are deterministic byte for byte for a given input and rate.

## [0.9.0] - 2025-06-24

### Added

- Strict validation: address shape, the 10 MiB cap on `data_len`, and
  duplicate addresses are all reported as parse errors with line
  numbers instead of aborting the run.
- CI runs the cross-engine parity gate on every push; a disagreement
  between the Python and TypeScript engines fails the build.

### Changed

- Parse errors no longer stop the audit; every bad line is collected
  and the good records are still summarised.

## [0.8.0] - 2024-06-04

### Added

- `docs/FORMAT.md`, `docs/RATE_SCHEDULE.md`, `docs/OPERATIONS.md` and
  `docs/ARCHITECTURE.md` document the input format, the rate variable,
  the operator workflow, and the module layout.
- A worked walkthrough with a real run of both engines joined the
  README.

### Fixed

- The owners table prints lamports without thousands separators when
  `--format json` is selected.

## [0.7.0] - 2023-04-18

### Added

- The reclaimable-on-close total and the underfunded deficit are part
  of every report, not just the JSON one.
- The owners table is ranked by locked lamports, highest first.

## [0.6.3] - 2022-06-14

### Fixed

- Rate presets reject zero and negative lamports-per-byte values with
  a usage error instead of dividing the snapshot into nonsense.
- Every parse error carries its line number in both report formats.

## [0.6.0] - 2022-02-08

### Added

- `--preset` selects a rate step by name, and `--lamports-per-byte`
  sets an explicit rate for the audit.
- The SIMD-0437 schedule steps from 6,960 down to 696 ship as named
  presets; 6,333 remains the documented mainnet default.

### Changed

