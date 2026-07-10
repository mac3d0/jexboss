# JexBoss enhanced fork

A JBoss and Java deserialization verification and exploitation tool, extended with a Shodan driven bulk scanning workflow and some quality of life improvements for larger engagements.

Maintained by Rafael Macedo. Contact rafael.macedo@brechasec.com.br and https://brechasec.com.br/

## What I added in this fork

The main addition is a new `shodan-scan` mode. It pulls candidate targets straight from the Shodan API through `shodan_search()`, with the flags `-shodan-query`, `-shodan-apikey`, `-shodan-limit` and `-shodan-results`. It talks to the API over the existing HTTP pool, so there is no extra pip dependency.

Before any Shodan bulk scan runs, there is an interactive authorization gate. The operator has to confirm they are allowed to test the collected targets. It is a scope and ethics check baked into the workflow.

I also added a bulk quiet mode through `gl_quiet`, which silences the per host noise during mass scans so the output stays readable, and a live progress bar through `print_progress_bar`, a single line indicator shared across the Shodan and file scan loops.

The full list is in CHANGELOG.md.

Example:

```bash
python jexboss.py -mode shodan-scan \
  -shodan-query 'product:JBoss' \
  -shodan-apikey YOUR_KEY \
  -shodan-results report_shodan_scan.log
```

## Legal and ethical use

This tool is for study and authorized security testing only. Use it against systems you own or have explicit written authorization to test, under a signed engagement scope. Scanning or exploiting third party systems without permission is illegal and can carry criminal and civil liability.

Do not commit real target lists, scan results or logs. The included .gitignore keeps log files, host lists and result files out of version control.

## Requirements

Python 2.7 or newer, plus urllib3 and ipaddress.

## Installation

```bash
git clone https://github.com/mac3d0/jexboss.git
cd jexboss
pip install -r requires.txt
python jexboss.py -h
```

## Usage

```bash
# Single host
python jexboss.py -host http://target_host:8080

# Bulk scan from a Shodan query, added in this fork
python jexboss.py -mode shodan-scan -shodan-query 'product:JBoss' -shodan-apikey YOUR_KEY

# All modes and options
python jexboss.py -h
```

## License

Licensed under the Apache License, Version 2.0. See the LICENSE file.

## Credits

This is built on top of JexBoss, originally created by João Filho Matos Figueiredo. The upstream project is at https://github.com/joaomatosf/jexboss and the CSV helper is by Sean Whalen. All upstream copyright and attribution notices are kept in the NOTICE file, as the license requires. The enhancements in this fork are by Rafael Macedo, 2026.
