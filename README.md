# JexBoss — Educational Fork

> **Fork for study and authorized security testing.**
> This is a maintained fork of the **JexBoss** tool. The original tool was created by
> **João Filho Matos Figueiredo ([@joaomatosf](https://github.com/joaomatosf/jexboss))** and is
> licensed under the Apache License 2.0. Full credit for the core tool belongs to the upstream author.
>
> **Improvements & maintenance of this fork:** Rafael Macedo · `rafael.macedo@brechasec.com.br`

JexBoss is a tool for testing and exploiting vulnerabilities in **JBoss Application Server** and other Java platforms, frameworks and applications (including several Java deserialization vulnerabilities).

---

## ⚠️ Legal & ethical notice

This tool is provided **strictly for educational purposes and authorized security testing**. Use it **only** against systems you own or for which you hold **explicit written authorization** (signed engagement scope). Unauthorized scanning or exploitation of third-party systems is illegal and may lead to criminal and civil liability. The maintainer and the original author assume no responsibility for misuse.

**Do not commit real target lists, scan results or logs to this repository** — the included `.gitignore` is configured to keep `*.log`, `hosts*.txt` and result files out of version control.

---

## Requirements

* Python >= 2.7.x
* [urllib3](https://pypi.python.org/pypi/urllib3)
* [ipaddress](https://pypi.python.org/pypi/ipaddress)

## Installation

```bash
git clone <this-repo-url>.git
cd jexboss
pip install -r requires.txt
python jexboss.py -h
```

## Usage

```bash
# Single host
python jexboss.py -host http://target_host:8080

# Full help / all modes
python jexboss.py -h
```

Additional modes supported by the tool include standalone/reverse-shell mode, auto-scan over a CIDR network (`-network`), and file-based scanning (`-file`). See `python jexboss.py -h` for the complete, up-to-date option list.

---

## Credits

* **Original tool:** João Filho Matos Figueiredo — <https://github.com/joaomatosf/jexboss> — `joaomatosf@gmail.com`
* **`jexcsv.py` component:** Sean Whalen (2016)
* **This educational fork:** Rafael Macedo — `rafael.macedo@brechasec.com.br` · [brechasec.com.br](https://brechasec.com.br/)

## License

Licensed under the **Apache License, Version 2.0** — see [`LICENSE`](LICENSE).
Attribution and a summary of modifications are recorded in [`NOTICE`](NOTICE), as required by the license.
