# NETWORK — Garnett Water & Power

## VMnets (VMware Workstation host-only)

| VMnet | VLAN | Subnet | Purpose | DHCP |
|-------|------|--------|---------|------|
| VMnet2 | 10 | 10.10.10.0/24 | Corporate | On (scoped) |
| VMnet3 | 20 | 10.10.20.0/24 | OT DMZ | Off |
| VMnet4 | 30 | 10.10.30.0/24 | Central OT | Off |
| VMnet5 | 51 | 10.10.51.0/24 | Water Plant | Off |
| VMnet6 | 52 | 10.10.52.0/24 | Pipeline Station | Off |
| VMnet7 | 53 | 10.10.53.0/24 | Substation | Off |

## Address plan

| Asset | IP | MAC | VMnet | Notes |
|-------|-----|-----|-------|-------|
| | | | | |

(Mirror of ASSET-INVENTORY — keep the network view here: gateways, DNS, NTP, macvlan container IPs.)

## Routing and emulation

- Single pfSense (FW-CORE) routes all zones; default-deny between them.
- Traffic limiters: 10 Mbps on site interfaces (WAN emulation). Measured effect: ___.
- Expansion path: split FW-IT / FW-OT — which rules move where (see FIREWALL-RULES.md §expansion).

## DNS and time

Windows → DC01. Linux/firewall → pfSense forwarder. NTP chain: ___.
Why time discipline matters here: (your one-paragraph answer — incident timelines depend on it)
