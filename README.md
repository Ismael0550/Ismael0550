<p align="center">
  <picture>
    <source media="(max-width: 600px)" srcset="assets/header-mobile.svg">
    <img src="assets/header.svg" alt="Ismael Saldivar: aspiring Linux systems administrator and network engineer" width="100%">
  </picture>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/ismael-saldivar-74a75b112/"><img src="https://img.shields.io/badge/LinkedIn-Ismael_Saldivar-0d1b2a?style=flat-square&labelColor=18222e&logo=linkedin&logoColor=58a6ff" alt="LinkedIn: Ismael Saldivar"></a>
  <a href="https://github.com/Ismael0550/homelab"><img src="https://img.shields.io/badge/homelab-Proxmox_VE_+_pfSense-0d1b2a?style=flat-square&labelColor=18222e&logo=proxmox&logoColor=3fb950" alt="Homelab: Proxmox VE and pfSense"></a>
  <img src="https://img.shields.io/badge/daily_driver-Fedora_KDE-0d1b2a?style=flat-square&labelColor=18222e&logo=fedora&logoColor=58a6ff" alt="Daily driver: Fedora KDE">
</p>

```console
ismael@fedora:~$ whoami
Ismael Saldivar
B.S. Computer Science @ UNT, May 2027
Tier 1 IT Support @ Van's Kitchen
Student IT @ UNT College of Engineering

ismael@fedora:~$ uname -a
Linux fedora-kde x86_64 GNU/Linux

ismael@fedora:~$ cat ~/focus.txt
Linux systems administration
Networking and network infrastructure
Virtualization and homelab infrastructure
Infrastructure automation

ismael@fedora:~$ ls ~/projects
homelab/
```
<sub>↑ Illustrative terminal, not live output from a real system.</sub>

## `$ ls /etc/skills`

| Area | How I've actually used it |
|---|---|
| **Linux systems administration** | Fedora KDE as my daily desktop, plus Ubuntu and other distros. Systemd services, journalctl and logs, processes, filesystems and permissions, package management, SSH remote administration, and Linux troubleshooting at work and in my lab |
| **Networking** | pfSense as the router and firewall for my lab: firewall rules, routing, DHCP, and DNS. Tailscale VPN for remote access. Proxmox network bridges and virtual NICs. Network and DNS troubleshooting on the job |
| **Virtualization & homelab** | Proxmox VE running Linux and Windows VMs plus Linux containers. GPU passthrough to a media server VM |
| **Windows Server & Active Directory** | AD Domain Services on Windows Server in my lab. Domain joins, AD administration, and Windows 11 imaging and deployment at work |
| **Infrastructure automation** | FOG Project imaging with automatic AD domain join, and agent deployment through FOG Snapins. ConnectWise RMM. PowerShell and Bash scripting |
| **Programming** | Python, C++, and SQL from coursework and projects. PowerShell and Bash for admin tasks |

<p>
  <img src="https://img.shields.io/badge/Linux-0d1b2a?style=flat-square&logo=linux&logoColor=3fb950" alt="Linux">
  <img src="https://img.shields.io/badge/Fedora-0d1b2a?style=flat-square&logo=fedora&logoColor=3fb950" alt="Fedora">
  <img src="https://img.shields.io/badge/Ubuntu-0d1b2a?style=flat-square&logo=ubuntu&logoColor=3fb950" alt="Ubuntu">
  <img src="https://img.shields.io/badge/Bash-0d1b2a?style=flat-square&logo=gnubash&logoColor=3fb950" alt="Bash">
  <img src="https://img.shields.io/badge/pfSense-0d1b2a?style=flat-square&logo=pfsense&logoColor=58a6ff" alt="pfSense">
  <img src="https://img.shields.io/badge/Tailscale-0d1b2a?style=flat-square&logo=tailscale&logoColor=58a6ff" alt="Tailscale">
  <img src="https://img.shields.io/badge/Proxmox_VE-0d1b2a?style=flat-square&logo=proxmox&logoColor=3fb950" alt="Proxmox VE">
  <img src="https://img.shields.io/badge/Windows_Server_/_AD-0d1b2a?style=flat-square" alt="Windows Server and Active Directory">
  <img src="https://img.shields.io/badge/PowerShell-0d1b2a?style=flat-square" alt="PowerShell">
  <img src="https://img.shields.io/badge/Python-0d1b2a?style=flat-square&logo=python&logoColor=58a6ff" alt="Python">
  <img src="https://img.shields.io/badge/C++-0d1b2a?style=flat-square&logo=cplusplus&logoColor=58a6ff" alt="C++">
</p>

## `$ systemctl status homelab`

```console
● homelab.service - Proxmox VE homelab
     Loaded: loaded (/etc/homelab/proxmox-ve)
     Active: active (running) since April 2026
       Docs: https://github.com/Ismael0550/homelab
```
<sub>↑ Illustrative, styled like systemctl output.</sub>

I built my homelab to get hands-on time with the systems I support at work, and with the networking side I don't get to configure there. It's a single **Proxmox VE** server where I build, break, and fix things:

- **Proxmox VE** hosts everything: Linux and Windows VMs, Linux containers, and a media server VM with GPU passthrough
- **pfSense** runs as a VM. It's the router, firewall, DHCP server, and DNS resolver for the lab network, and keeps the lab separate from my home network
- **Windows Server** runs an Active Directory domain I use to practice the AD work I do on the job
- **Linux guests** are where I practice services, permissions, logs, and troubleshooting on server distros
- **Tailscale** runs on pfSense, so I can reach the lab securely when I'm away from home

```mermaid
flowchart LR
    NET((Internet)) --> HR[Home router]
    HR --> PF
    REMOTE[My laptop / phone] -. Tailscale VPN .-> PF
    subgraph PVE[Proxmox VE host]
        PF[pfSense VM<br/>firewall · routing · DHCP · DNS · Tailscale] --> LAN[Lab network]
        LAN --> DC[Windows Server<br/>AD DS]
        LAN --> LNX[Linux VMs & containers]
        LAN --> MEDIA[Media server VM<br/>GPU passthrough]
    end
```

**What I'm learning from it:** routing and firewall policy, running DHCP and DNS, working behind double NAT, VPN remote access, Proxmox bridges and virtual NICs, PCIe passthrough, and building an AD domain from scratch.

**Full documentation:** [Ismael0550/homelab](https://github.com/Ismael0550/homelab)

## `$ history | grep deploy`

What I do on the job, described without employer configurations or internal details.

**Van's Kitchen, Tier 1 IT Support** (Sep 2026 – present)
- I improved the company's existing **FOG Project** imaging setup on my own. New Windows workstations now **join Active Directory automatically** during deployment.
- Automated endpoint management and security agent deployment with **FOG Snapins**
- Troubleshot image capture failures, permissions, deployment configuration, and Windows provisioning
- Endpoint management with **ConnectWise RMM**, plus day-to-day IT operations

**UNT College of Engineering, Student IT**
- Windows 11 imaging and deployment, **Active Directory** administration, and domain joins
- **Linux and Windows troubleshooting**, plus OS, network, and enterprise application issues for faculty, staff, and computer labs
- PowerShell scripting and software deployment

## `$ ls ~/projects/planned`

These aren't built yet. I'll publish each one when it has real, working content.

| Project | Status | Scope |
|---|---|---|
| `linux-admin-toolkit` | 🟡 planned | Bash scripts and docs for disk and filesystem checks, systemd service status, journalctl log triage, process and resource monitoring, network interface and DNS diagnostics, SSH administration, and system health checks |
| `networking-lab` | 🟡 planned | pfSense, routing, firewall rules, DNS and DHCP, bridges, VPN, troubleshooting, and diagrams, all from my lab |
| `infra-automation` | 🟡 planned | Sanitized lab examples of PowerShell and Bash provisioning, Windows deployment, and AD automation (no employer scripts) |

## `$ ping ismael`

<a href="https://www.linkedin.com/in/ismael-saldivar-74a75b112/"><img src="https://img.shields.io/badge/Connect_on_LinkedIn-0d1b2a?style=for-the-badge&logo=linkedin&logoColor=58a6ff" alt="Connect on LinkedIn"></a>
