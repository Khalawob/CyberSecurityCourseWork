# Lab 4: Nessus

## Overview

This lab used Nessus to perform vulnerability assessment against two systems:

- a WordPress server
- an MSC gateway server

The scans were configured to identify web vulnerabilities and open ports so that the systems could be compared.

## WordPress Scan

The WordPress server scan identified several findings, including medium-risk and low-risk issues. Examples included:

- WordPress user enumeration
- clickjacking-related weaknesses
- browsable web directories
- SSH Terrapin Prefix Truncation Weakness
- ICMP timestamp information disclosure
- cookie security flag issues
- framing policy weaknesses

### Example summary table

| Vulnerability | Description | Effect | Mitigation |
|---|---|---|---|
| SSH Terrapin Prefix Truncation Weakness | Protocol-level SSH weakness during session setup | Weakens SSH integrity | Update SSH |
| Browsable Web Directories | Directory listing enabled | Exposes files and structure | Disable listing and harden configuration |
| Potential Clickjacking | Application may be framed | Users could be tricked into unauthorized actions | Use `Content-Security-Policy` and `X-Frame-Options` |
| WordPress User Enumeration | Valid usernames are exposed | Supports brute-force and phishing | Reduce exposure and enforce MFA |
| ICMP Timestamp Disclosure | System time is disclosed | Assists reconnaissance | Disable timestamp responses where appropriate |

## MSC Gateway Scan

The MSC gateway scan identified far fewer issues and mainly reported the ICMP timestamp disclosure finding.

## Analysis and Comparison

The WordPress server appeared less secure because it had more findings, but this was heavily influenced by how the environment had been configured. The WordPress server had intentionally vulnerable plugins and themes installed, as well as more exposed services such as SSH.

The MSC gateway appeared cleaner largely because it exposed less software and fewer attack paths.

This shows why raw vulnerability counts must be interpreted in context.

## Reflection

This lab showed how Nessus can generate professional vulnerability reports and support risk prioritisation. It also demonstrated that comparing systems requires context rather than relying only on the total number of findings.

## Strengths and Weaknesses

### Strengths

- Professional reporting
- Useful severity scoring
- Updated plugin-based detection

### Weaknesses

- Mitigations may require separate research
- Initial setup and plugin compilation can take time
- Findings need context to be interpreted correctly

## References

1. GeeksforGeeks, “SSH Port Forwarding.”
2. GeeksforGeeks, “Introduction to SSH (Secure Shell) Keys.”
3. GeeksforGeeks, “SCP Command in Linux with Examples.”
4. GeeksforGeeks, “Types of Multiplexing in Data Communications.”
5. OWASP Foundation, “A03:2021 – Injection.”
6. PortSwigger, “SQL Injection.”
7. WPScan, “WPScan User Documentation.”
8. OWASP Foundation, “OWASP Juice Shop Project.”
9. PortSwigger, “Burp Suite Documentation.”
10. Tenable, “Nessus Product Overview.”

## Add screenshots

```md
![Nessus WordPress dashboard](assets/lab4-wordpress-dashboard.png)
![Nessus gateway dashboard](assets/lab4-gateway-dashboard.png)
```
