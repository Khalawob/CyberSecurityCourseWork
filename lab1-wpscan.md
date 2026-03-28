# Lab 1: WPScan

## Overview

This lab focused on setting up a WordPress security assessment environment using WPScan on Kali Linux against a WordPress virtual machine. The objective was to configure the environment, enumerate plugins and themes, identify known vulnerabilities, and test password security.

## Environment Setup

A new administrator account was created in WordPress so plugins and themes could be installed and configured. Weak credentials were deliberately used for testing in the controlled lab environment.

Vulnerable plugins and themes were then installed to create a realistic target for WPScan.

## WPScan Usage

The WPScan database was updated first so the scanner had current vulnerability data available.

An API token was connected to WPScan so the scan results could be matched against the online vulnerability database.

Example commands used:

```bash
wpscan --url http://192.168.123.65 --enumerate vp,vt,tt
wpscan --url http://192.168.123.65 --passwords /home/kali/Desktop/passwords.txt --usernames Brian
wpscan --api-token YOUR_TOKEN --url http://192.168.123.65 --enumerate ap
```

## Findings

The scan identified:

- the active WordPress theme
- vulnerable plugins
- multiple plugin vulnerabilities
- a reflected cross-site scripting issue in the installed theme
- a weak password that could be discovered with a wordlist

The output showed that the account **Brian** with the password **admin** could be brute-forced successfully.

## Security Implications

The identified vulnerabilities created a serious security risk because exploit information is publicly available for many WordPress issues. Weaknesses such as SQL injection, stored cross-site scripting, reflected cross-site scripting, and sensitive information disclosure could lead to:

- theft of user data
- account compromise
- malicious content injection
- wider compromise of the web application

The most direct mitigation was to update plugins and themes to current versions and avoid weak credentials.

## Comparison of Enumeration Modes

| Mode | Purpose | Speed |
|---|---|---|
| `vp` | Scans vulnerable plugins only | Faster |
| `vt` | Scans vulnerable themes only | Faster |
| `ap` | Scans all plugins | Slower |
| `tt` | Scans themes and attempts to find related vulnerabilities | Slower |

## Further Learning: Exploiting a Vulnerability

A stored cross-site scripting issue in a salon plugin was demonstrated. By modifying a plugin field and inserting a payload such as:

```html
<img src=x onerror=alert(1)>
```

it was possible to trigger script execution when the malicious content was rendered in the application.

This demonstrated the importance of input validation, output encoding, and prompt patching of outdated plugins.

## Reflection

This lab demonstrated how WordPress plugins and themes can introduce substantial risk when they are not updated. It also showed the trade-off between targeted scanning and broader scanning, and highlighted the value of WPScan's online vulnerability database when used with an API token.

## Strengths and Weaknesses

### Strengths

- Strong coverage of known WordPress vulnerabilities
- Useful CVE references and version information
- Practical enumeration options for plugins and themes

### Weaknesses

- Limited to WordPress
- Cannot identify zero-day vulnerabilities reliably
- API usage is rate-limited

## Add screenshots

Place exported screenshots in `assets/` and reference them here, for example:

```md
![WPScan identified plugin vulnerabilities](assets/lab1-wpscan-plugin-vulns.png)
```
