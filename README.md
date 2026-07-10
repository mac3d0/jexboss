# JexBoss — Enhanced Fork

JBoss (and Java deserialization) verification & exploitation tool, extended with a **Shodan-driven bulk scanning workflow** and quality-of-life improvements for large engagements.

**Maintained by Rafael Macedo** · `rafael.macedo@brechasec.com.br` · [brechasec.com.br](https://brechasec.com.br/)

---

## ✨ Improvements in this fork

These features were designed and implemented on top of the base tool:

| Feature | Description |
|---------|-------------|
| **`shodan-scan` mode** | New operation mode that pulls candidate targets directly from the **Shodan API** (`shodan_search()`), with dedicated flags `-shodan-query`, `-shodan-apikey`, `-shodan-limit` and `-shodan-results`. No extra pip dependency — talks to the API over the existing HTTP pool. |
| **Interactive authorization gate** | Before any Shodan-driven bulk scan runs, an explicit **authorization prompt** requires the operator to confirm they are permitted to test the collected targets — an ethics/scope guardrail baked into the workflow. |
| **Bulk quiet mode (`gl_quiet`)** | Silences noisy per-host output during mass scans so results stay readable. |
| **Live progress bar** | Single-line, in-place progress indicator (`print_progress_bar`) for bulk/file scan loops, shared across the Shodan and file-interactive views. |

See [`CHANGELOG.md`](CHANGELOG.md) for the full list.

### Example

```bash
python jexboss.py -mode shodan-scan \
  -shodan-query 'product:JBoss' \
  -shodan-apikey YOUR_KEY \
  -shodan-results report_shodan_scan.log
```

---

## ⚠️ Legal & ethical notice

This tool is provided **strictly for educational purposes and authorized security testing**. Use it **only** against systems you own or for which you hold **explicit written authorization** (signed engagement scope). Unauthorized scanning or exploitation of third-party systems is illegal and may lead to criminal and civil liability.

**Do not commit real target lists, scan results or logs** — the included `.gitignore` keeps `*.log`, `hosts*.txt` and result files out of version control.

---

## Requirements

* Python >= 2.7.x
* [urllib3](https://pypi.python.org/pypi/urllib3) · [ipaddress](https://pypi.python.org/pypi/ipaddress)

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

# Bulk scan from a Shodan query (this fork)
python jexboss.py -mode shodan-scan -shodan-query 'product:JBoss' -shodan-apikey YOUR_KEY

# All modes and options
python jexboss.py -h
```

---

## License

Licensed under the **Apache License, Version 2.0** — see [`LICENSE`](LICENSE).

## Credits

Built on top of **JexBoss**, originally created by João Filho Matos Figueiredo ([upstream project](https://github.com/joaomatosf/jexboss)); CSV helper by Sean Whalen. All upstream copyright and attribution notices are retained in [`NOTICE`](NOTICE), as required by the license. Enhancements in this fork © 2026 Rafael Macedo.
