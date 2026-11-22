# Lab 1: Metasploitable 2 Recon & Bindshell Verification

## Environment
- Attacker: Kali Linux (host-only adapter)
- Target: Metasploitable 2 (`192.168.56.102`, host-only adapter)

## What I Scanned
Ran `nmap -sV 192.168.56.102 -oN scan1.txt` to identify open TCP ports and service versions.

## Key Findings
- **Port 1524/tcp (bindshell):** Accepted an unauthenticated connection via `nc 192.168.56.102 1524` and gave an immediate root shell.
- **Other exposed legacy services:** Samba (`139`, `445`), ProFTPD 1.3.1 (`2121`), MySQL (`3306`), PostgreSQL (`5432`), VNC (`5900`), and UnrealIRCd (`6667`).

## Remediation
- Close port 1524 and remove the bindshell backdoor.
- Disable services that aren't needed.
- Upgrade outdated software to supported versions.
- Restrict access with host-based firewall rules (`ufw`/`iptables`).
- Keep intentionally vulnerable targets isolated on a host-only network.
