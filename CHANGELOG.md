# Changelog

Changes made in this fork on top of the upstream JexBoss by João Filho Matos Figueiredo, at https://github.com/joaomatosf/jexboss

## Fork, 2026

Added a `shodan-scan` operation mode. It collects candidate targets from the Shodan API through `shodan_search()`, with the new flags `-shodan-query`, `-shodan-apikey` or the `SHODAN_API_KEY` env var, `-shodan-limit` and `-shodan-results`. It runs over the existing HTTP pool and needs no extra pip dependency.

Added an interactive authorization gate to the Shodan bulk scan workflow. The operator has to confirm authorization before any target collected from Shodan is scanned.

Added a live progress bar through `progress_bar_str` and `print_progress_bar`, a single line indicator shared across the bulk and file scan loops.

Added a bulk quiet mode through `gl_quiet`. It hides the per host output during mass scans so the progress bar and the final findings stay readable. The full per vector detail is printed after the sweep finishes.

Rewrote the documentation to focus on the fork specific features.

Added a .gitignore so real target lists, scan results and logs never get committed. It covers log files, host lists and result files.

Added a NOTICE file with the upstream attribution and the list of modifications made here, as the Apache License 2.0 requires.

Upstream author João Filho Matos Figueiredo, Apache 2.0. Fork enhancements by Rafael Macedo, 2026, rafael.macedo@brechasec.com.br
