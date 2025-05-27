# iOSVulnLab – An Intentionally Vulnerable iOS App (2023)

[![OWASP](https://img.shields.io/badge/Standard-OWASP%20MASVS%20%26%20MASTG-FF6600?style=flat-square)](https://mas.owasp.org/)

> A sandbox application designed to teach and test iOS security vulnerabilities using OWASP MASVS and MASTG guidelines.

---

## Table of Contents

* [Overview](#overview)
* [Features & Vulnerabilities](#features--vulnerabilities)
* [Prerequisites](#prerequisites)
* [Testing Scenarios](#testing-scenarios)
* [OWASP References](#owasp-references)
* [Contributing & Contact](#contributing--contact)

---

## Overview

iOSVulnLab is an intentionally vulnerable iOS application that demonstrates common security mistakes and anti-patterns. It serves as a hands‑on lab for students, pentesters, and developers to practice:

* **Static Analysis** – source code flaws, insecure storage, weak encryption, improper configuration.
* **Dynamic Analysis** – runtime vulnerabilities: insecure network calls, injection, insecure authentication.

Clone the repo and use the OWASP Mobile Security Testing Guide (MASTG) & Mobile Application Security Verification Standard (MASVS) to break it and identify vulnerabilities.

---

## Features & Vulnerabilities

| Feature                           | Intentional Vulnerability                                                         |
| --------------------------------- | --------------------------------------------------------------------------------- |
| Keychain Misuse                   | Storing sensitive tokens in unprotected keychain items (no access control)        |
| Insecure UserDefaults             | Secrets and flags stored in UserDefaults with predictable keys                    |
| Info.plist Exposure               | API endpoints and app secrets exposed in Info.plist                               |
| Plain-text Secrets                | Hard-coded API keys and credentials within source code                            |
| Improper SSL Pinning              | ATS disabled and no certificate pinning on HTTPS requests                         |
| Vulnerable SFSafariViewController | Unrestricted `SFSafariViewController` allowing malicious redirects                |
| JS Injection in Web Views         | Injectable JavaScript in embedded WKWebView without content filtering             |
| Insecure Logging                  | Verbose logging of sensitive data and errors                                      |
| Broken Access Control             | Role and permission checks bypassable via manipulated parameters                  |
| Easter Eggs & Hidden Flaws        | Hidden debug menus, backdoor API endpoints, and undocumented features to discover |

---

## Prerequisites:

1. Physical iOS device or emulator (Simulator won’t cut it; consider using Corellium).
2. Jailbroken device for deeper testing of low-level and patched security controls.

---

## Testing Scenarios
###  (spoiler alert)

Use these steps alongside the OWASP MASTG chapters:

1. **Static Analysis**

   * Inspect source for hard‑coded API keys, insecure defaults, improper crypto usage.
   * Tools: `grep`, `MobSF`, `Frida`, ...

2. **Dynamic Analysis**

   * Intercept HTTP(S) calls (e.g., BurpSuite proxy) – verify absence of ATS enforcement.
   * Tamper with authentication headers / JWT payloads.
   * Trigger insecure logging and inspect logs for secrets.

3. **Local Storage Tests**

   * Examine `UserDefaults`, Keychain, and local files for sensitive data.
   * Attempt SQL injection on local SQLite database.

4. **Access Control Checks**

   * Modify in‑app parameters to access protected screens or data.

Document your findings and map each to the corresponding MASVS control or MASTG test case.

---

## OWASP References

* [**MASVS**: Mobile Application Security Verification Standard]((https://mas.owasp.org/MASVS/))
* [**MASTG**: Mobile Application Security Testing Guide](https://mas.owasp.org/MASTG/)

---

## Contributing & Contact

Feel free to fork, add new vulnerable scenarios, and submit pull requests.
If you need help or have questions, reach out:

**Marko Lihter** – [lihter.marko@gmail.com](mailto:lihter.marko@gmail.com)

---

*Disclaimer: This application is intentionally insecure and should only be used in a controlled, legal testing environment.*
