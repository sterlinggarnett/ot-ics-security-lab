# Lab notes — explanations (HARD GATE journal)

> RULE: written AFTER building and observing, in your own words. No copy-paste from docs. If you can't explain it, you haven't finished the task.

---

### 2026-09-08 — Stage 1.2 / 1.3 — FW-CORE Interface & VMware VMnets Build

WHAT I OBSERVED:
* Today I configured the six VMnets for my OT/ICS lab in VMware. I then configured pfSense and mapped `em0`–`em5` to their corresponding VMnets using the MAC addresses of the virtual network adapters. This gives each Purdue Model zone its own isolated virtual network.

WHY IT HAPPENED:
* **MAC Address Correlation**: Necessary because VMnet numbers do not automatically correspond to pfSense `emX` interface numbers. I created a table matching each VMnet to its MAC address so I could accurately identify which VMware adapter was connected to each pfSense interface.
* **Disabling VMware DHCP on VMnets 3–7**: OT/ICS networks need predictable and controlled addressing. Critical systems such as PLCs, RTUs, and HMIs require fixed IP addresses so firewall rules can be written against specific systems. Disabling VMware DHCP also prevents VMware from independently assigning addresses, leaving pfSense responsible for routing and network control.

WHAT IT MEANS FOR SECURITY:
* **Host-Only Isolation & Routing Control**: Each network needs to remain isolated so traffic between zones is forced through pfSense. If a PLC had another virtual NIC connected directly to a different VMnet, that connection could potentially bypass the firewall and allow traffic between security zones without being inspected or controlled by pfSense.

---

### 2026-09-10 — Stage 1.3 — pfSense WebConfigurator Connectivity & Host Adapter Configuration

WHAT I OBSERVED:
* Configured host virtual adapter IPs on Windows host: `VMnet2` host adapter set to `10.10.10.2` and `VMnet3` host adapter enabled in VMware Virtual Network Editor and assigned `10.10.20.2` in Windows.
* Pinging `10.10.20.1` (pfSense `LAN` / `em1`) from host `10.10.20.2` succeeded with 0% packet loss, confirming Layer 3 network connectivity between the Windows host and pfSense.
* Browser access to `https://10.10.20.1` timed out on initial connection attempt.

WHY IT HAPPENED:
* **Host Virtual Adapter on VMnet3**: Temporarily enabling the host virtual adapter on `VMnet3` allows the Windows host machine to interface directly with pfSense's `LAN` (`10.10.20.1`), where pfSense's default Anti-Lockout rule permits ICMP ping and webConfigurator access.
* **Ping Success vs. Web Timeout**: ICMP ping operates at Layer 3 (IP), proving physical/virtual network link and routing work. WebConfigurator operates at Layer 7 (HTTPS / TCP 443). The HTTP timeout can be caused by pfSense webConfigurator service needing a restart or browser SSL/TLS certificate handling.

WHAT IT MEANS FOR SECURITY & ARCHITECTURE:
* **Temporary Management Access vs. Final Architecture**: Enabling host virtual adapters on OT subnets (`VMnet3`) is a temporary bootstrapping measure for initial lab setup. In final Purdue Model architecture, host adapters on OT subnets are disabled to enforce strict zero-trust network boundaries, forcing all management access to pass through DMZ Jump Hosts (`JUMP-01`).


