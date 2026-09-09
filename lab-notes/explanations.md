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

