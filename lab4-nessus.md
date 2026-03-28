# LAB 4: (Nessus)



Installing Nessus



Figure 136 - Nessus installation process shown in the terminal



Nessus initializing





Figure 137 - Nessus initialization page

Wordpress Configuration



Figure 138 - WordPress scan target configuration in Nessus



Scan configuration 



Figure 139 - WordPress scan type configuration in Nessus



Scan Type Configuration



Figure 140 - WordPress scan plugin settings in Nessus

## WordPress Report

I did a network scan of the WordPress server using it’s IP address and scanned for all web vulnerabilities and all ports to locate as much vulnerabilities as possible. 4 medium risk issues were found on WordPress such as user enumeration, clickjacking, browsable web directories and ssh terrapin previx truncation weakness. The low-risk issue was a timestamp request data disclosure. Below is a table containing details about the vulnerabilities found, security implications and some countermeasures.



| Vulnerability | Brief description | Effect on the system | Mitigation strategies |
| --- | --- | --- | --- |
| SSH Terrapin Prefix Truncation Weakness (CVE-2023-48795) | A protocol-level SSH weakness affecting certain SSH implementations during encrypted session setup. | Weakens the Integrity of SSH Connection. | Update SSH |
| Browsable Web Directories | Directory listing is enabled, allowing users to see the contents of web-accessible folders. | Attackers can discover backup files, scripts, uploads, other sensitive content that should not be public. | Disable directory listing using Options -Indexes, Update Plugins and themes |
| Web Application Potentially Vulnerable to Clickjacking | The application may be embeddable inside a malicious iframe, allowing deceptive user interaction. | Users could be tricked into clicking hidden or disguised elements, leading to unauthorized actions. | Set Content-Security-Policy: frame-ancestors and X-Frame-Options appropriately, such as DENY or SAMEORIGIN <br> |
| WordPress User Enumeration | The expose valid WordPress usernames  | Makes brute-force attacks, credential stuffing and phishing easier | Block enumeration vectors, restrict user exposure through the REST API, remove predictable usernames, and enforce MFA and rate limiting.<br> |
| ICMP Timestamp Request Remote Date Disclosure | The host responds to ICMP timestamp requests and reveals system time information. | Assists attackers with fingerprinting and reconnaissance, though it is usually low impact by itself. | Disable ICMP timestamp responses at the host or firewall level where operationally appropriate. |
| Missing or Permissive Content-Security-Policy frame-ancestors Header | The server does not properly restrict which sites are allowed to frame the application. | Increases clickjacking exposure and weakens browser-side UI protection. | Add a restrictive CSP header such as frame-ancestors 'none' or 'self' based on application requirements. |
| Missing or Permissive X-Frame-Options Header | The application does not send a strong anti-framing header. | Browsers may allow the site to be loaded in frames, increasing clickjacking risk. | Configure X-Frame-Options: DENY or SAMEORIGIN and keep it aligned with the CSP framing policy. |
| SSH Password Authentication Accepted | The SSH service allows password-based logins. | Expands the attack surface for brute-force attacks, password spraying, and credential reuse attacks. | Disable password authentication, require SSH keys, disable direct root login, and restrict SSH access by IP if needed. |
| Web Application Cookies Not Marked HttpOnly | Some cookies can potentially be accessed by client-side scripts. | If cross-site scripting is ever present, session cookies may be easier to steal or abuse. | Mark session and authentication cookies as HttpOnly,  |
| Web Application Cookies Not Marked Secure | Some cookies may be sent without being restricted to HTTPS transport. | Increases the risk of cookie exposure over insecure connections. | Enforce HTTPS everywhere |



Figure 141 - Tenable Nessus WordPress report cover page



Figure 142 - Nessus WordPress vulnerability summary dashboard

















MSC Gateway Configuration



Figure 143 - MSC Gateway target configuration in Nessus



Ubuntu Gateway Scan Type Configuration



Figure 144 - Ubuntu MSC Gateway scan type configuration in Nessus



Ubuntu MSC Gateway Scan type 



Figure 145 - Ubuntu MSC Gateway plugin settings in Nessus

## MSC Gateway report

I did a network scan of the Gateway server using it’s IP address and scanned for all web vulnerabilities and all ports to locate as much vulnerabilities as possible. The MSC Gateway report only located 1 vulnerability which was low risk. Below is a table containing some information about the vulnerability and security implications it could have.



| Vulnerability | Brief description | Effect on the system | Mitigation strategies |
| --- | --- | --- | --- |
| ICMP Timestamp Request Remote Date Disclosure | The host responds to ICMP timestamp requests and reveals system time information. | Assists attackers with fingerprinting and reconnaissance, though it is usually low impact by itself. | Disable ICMP timestamp responses at the host or firewall level where operationally appropriate. |



Figure 146 - Tenable Nessus MSC Gateway report cover page



Figure 147 - Nessus MSC Gateway vulnerability summary dashboard

## Analysis and Comparison of both reports

As a reminder, the WordPress server had 4 medium risk vulnerabilities and 1 low risk vulnerability while the MSC gateway only had 1 vulnerability which was low risk and the same as one of the risks in the WordPress server. If the 2 reports are compared with each other, it seems as if the MSC Gateway is more secure, but this is because the MSC Gateway hasn’t been modified with as much as the WordPress server because the WordPress Server has SSH Enabled and the fact that vulnerable plugins and themes have been purposely installed on WordPress. If the plugins and themes are updated, then it’s likely that the amount of WordPress vulnerabilities will be patched and will be able to gain a fairer evaluation.



## Reflection

This lab has taught how to use Nessus to identify local and remote vulnerabilities using their network scan and create professional reports that discuss the vulnerabilities and how to locate them. While the scan of the MSC Gateway at 192.168.123.1 revealed only one low-risk item, the WordPress server at 192.168.123.65 revealed four medium-level issues plus one minor issue. The comparison of the numbers across systems, rather than the numbers themselves is more important. The gateway appears to be more secure but is unlikely to be true because there are fewer alerts due to less software running and fewer ports open, which reduces the possibilities of issues. but on the other hand, the WordPress system is loaded with vulnerable plugins on purpose to test vulnerabilities which improves the risk level. This difference is important because, unless the actual context and background of the systems is taken into consideration, the amount of risks won't reveal which system is safer.





Strengths and Weaknesses

Professional reports can be generated and include CVSS scores and risk level which is essential for prioritizing action based on risk. The plugin architecture means the vulnerability data is constantly being updated and matching findings with the latest information. Nessus does not provide mitigation strategies within the report and must be researched separately on the website. When setting up Nessus downloading and compiling the plugins can take a very long time and Nessus scans can’t be used until the plugins have finished compiling


