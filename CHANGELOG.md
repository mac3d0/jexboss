# Changelog

All notable changes made in this fork, relative to the upstream
[JexBoss](https://github.com/joaomatosf/jexboss) by João Filho Matos Figueiredo.

## [fork] — 2026

### Added
- **`shodan-scan` operation mode** — collects candidate targets directly from the
  Shodan API via `shodan_search()`, with new CLI flags:
  `-shodan-query`, `-shodan-apikey` (or `SHODAN_API_KEY` env var), `-shodan-limit`
  and `-shodan-results`. Implemented over the existing HTTP pool, with no
  additional pip dependency.
- **Interactive authorization gate** for the Shodan bulk-scan workflow, requiring
  the operator to explicitly confirm authorization before any target collected
  from Shodan is scanned.
- **Live progress bar** (`progress_bar_str`, `print_progress_bar`) for bulk and
  file-based scan loops — a single-line, in-place indicator shared across the
  Shodan and file-interactive views.

### Changed
- **Bulk quiet mode (`gl_quiet`)** — suppresses per-host output during mass scans
  so the progress bar and final findings stay readable; full per-vector detail is
  printed after the sweep completes.
- Documentation rewritten to highlight fork-specific features.

### Housekeeping
- Added `.gitignore` to prevent committing real target lists, scan results and
  logs (`*.log`, `hosts*.txt`, `results*`).
- Added `NOTICE` documenting upstream attribution and the modifications made in
  this fork, as required by the Apache License 2.0.

---

Upstream original author: João Filho Matos Figueiredo · Apache-2.0.
Fork enhancements © 2026 Rafael Macedo <rafael.macedo@brechasec.com.br>.
