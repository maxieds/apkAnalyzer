<div align="center">

# APK Analyzer

### Know what ships inside your APK.

Find risky settings, spot potential secrets, and turn Android app analysis into shareable reports.

[![Download latest release](https://img.shields.io/badge/Download-latest_release-2ea44f?style=for-the-badge)](https://github.com/worldtreeboy/apkAnalyzer/releases/latest)
[![Star on GitHub](https://img.shields.io/badge/Star_on_GitHub-facc15?style=for-the-badge&logo=github&logoColor=black)](https://github.com/worldtreeboy/apkAnalyzer)

[![CI](https://github.com/worldtreeboy/apkAnalyzer/actions/workflows/ci.yml/badge.svg)](https://github.com/worldtreeboy/apkAnalyzer/actions/workflows/ci.yml)
![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-3776AB?logo=python&logoColor=white)
[![MIT License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

Windows · Linux · WSL · macOS

</div>

## One app. A closer look.

- **Inspect what matters.** Manifest settings, permissions, exported components, network policies, signing, code patterns, and potential hardcoded secrets.
- **Get evidence you can use.** Severity, confidence, remediation, and source locations where available. Missing coverage is marked `INCONCLUSIVE`.
- **Take the report with you.** HTML for review, JSON for automation, SARIF for CI.
- **Go deeper on a device.** Storage audits, runtime checks, logcat, screenshots, and Frida integration.

Supports `.apk`, `.apks`, `.aab`, and split-APK folders. Local scans need no connected phone. The core uses only Python's standard library.

## From APK to report

Install **Python 3.8+, Java, and [apktool](https://apktool.org/docs/install/)**. Add **apksigner** to `PATH` for signing verification; missing signing evidence makes coverage incomplete.

[Download the release ZIP](https://github.com/worldtreeboy/apkAnalyzer/releases/latest), extract it, and open a terminal in that folder. Keep `apkAnalyzer.py` beside `apk_analyzer/`.

```bash
python3 apkAnalyzer.py scan --apk app.apk --format html --output report.html
```

Open **`report.html`** to explore the results. On Windows, use `python` if that's your Python command.

<details>
<summary><strong>CI, App Bundles, and connected devices</strong></summary>

**CI:** export SARIF and fail on high-severity findings.

```bash
python3 apkAnalyzer.py scan --apk app.apk --format sarif --output report.sarif --fail-on high
```

Exit codes: `0` = no findings meet the threshold; `1` = threshold met; `2` = scan failed or evidence incomplete. Incomplete coverage takes precedence. A completed scan does not establish that an app is vulnerability-free.

**App Bundles:** use `--apk app.aab --bundletool /path/to/bundletool.jar`. Dynamic-feature coverage may be incomplete.

**Device mode:** install ADB, enable USB debugging, connect your phone, and run `python3 apkAnalyzer.py`. Some features need root or Frida. Use `[r]` to export reports.

**More options:** `python3 apkAnalyzer.py scan --help`

**Run the tests:** `python3 -m unittest discover -s tests -q`

</details>

---

**Saved you time? [Give APK Analyzer a star ⭐](https://github.com/worldtreeboy/apkAnalyzer).** It helps others find the project.

[Report a bug](https://github.com/worldtreeboy/apkAnalyzer/issues) · [Release notes](https://github.com/worldtreeboy/apkAnalyzer/releases) · [Contribute a fix](https://github.com/worldtreeboy/apkAnalyzer/pulls)
