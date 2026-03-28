# Lab 3: Nmap and SSH

## Overview

This lab covered two major areas:

1. network scanning and reconnaissance with Nmap
2. secure remote administration and file transfer with SSH, SCP, and SFTP

---

## Part 1: Nmap

### Host Discovery and Basic Scans

The lab demonstrated several scan types:

- ping scan
- single host scan
- multi-host scan
- subnet scan

These scans showed whether hosts were alive, which ports were open, and how Nmap output changes depending on scope.

### Port and Scan Types

The following scan techniques were explored:

- TCP connect scan
- SYN scan
- UDP scan
- port range scan
- specific port scan

These highlighted trade-offs between speed, stealth, and required privileges.

### Detection and Enumeration

Additional scans included:

- service/version detection
- operating system detection
- aggressive scanning
- NSE vulnerability scripts
- targeted NSE scripts such as `http-enum`

### Output Formats

The scan results were saved as:

- text output
- XML
- greppable format

This showed how Nmap can support both manual analysis and automation.

### Advanced Scanning Techniques

The lab also explored:

- decoys
- fragmentation
- MAC spoofing
- idle scans
- timing templates
- traceroute
- IPv6 scanning
- ACK scans
- host discovery limited to systems with open ports

## Part 2: SSH

### SSH Basics

SSH was used to connect to a remote host and specify ports manually where needed.

### Authentication and Key Management

The following tasks were completed:

- generating a 4096-bit RSA key pair
- copying the public key to a remote server
- logging in without a password

### Session Management

The lab also demonstrated:

- logging out
- executing remote commands
- SSH multiplexing and persistent connections
- verbose mode for debugging
- using an alternative private key

### Secure File Transfer

Two secure file transfer approaches were tested:

- **SCP** for direct copying between systems
- **SFTP** for interactive remote file management

A comparison showed that SFTP is often more convenient when managing files interactively, while SCP is efficient for direct transfers.

### Port Forwarding

The lab covered:

- local port forwarding with `-L`
- remote port forwarding with `-R`

These techniques are useful for securely tunnelling traffic through SSH.

## Reflection

This lab showed that no scan type or remote access method is universally best. Nmap options involve trade-offs between coverage, speed, stealth, and required privileges. SSH-related tools demonstrated the importance of encrypted remote access, strong authentication, and secure file movement.

The Nmap NSE scripts also showed how reconnaissance can move into targeted vulnerability assessment.

## Strengths and Weaknesses

### Nmap strengths

- Highly flexible
- Supports many scan types
- Excellent scripting support
- Strong output format support

### Nmap weaknesses

- Less reliable through firewalls and filtering devices
- Some scan types require elevated privileges
- OS detection may be inaccurate in heavily filtered networks

### SSH strengths

- Encrypts traffic over untrusted networks
- Supports secure remote administration
- Enables secure tunnelling and file transfer

### SSH weaknesses

- Can be weakened by poor key management or password-based authentication
- Misconfiguration can create unnecessary exposure

## Add screenshots

```md
![Nmap SYN scan](assets/lab3-nmap-syn-scan.png)
![SSH key generation](assets/lab3-ssh-keygen.png)
```
