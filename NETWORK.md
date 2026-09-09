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
| FW-CORE (`em0`) | 10.10.10.1 | 00:0C:29:69:90:6C | VMnet2 | Corporate Gateway |
| FW-CORE (`em1`) | 10.10.20.1 | 00:0C:29:69:90:76 | VMnet3 | OT DMZ Gateway |
| FW-CORE (`em2`) | 10.10.30.1 | 00:0C:29:69:90:80 | VMnet4 | Central OT Gateway |
| FW-CORE (`em3`) | 10.10.51.1 | 00:0C:29:69:90:8A | VMnet5 | Water Plant Gateway |
| FW-CORE (`em4`) | 10.10.52.1 | 00:0C:29:69:90:94 | VMnet6 | Pipeline Station Gateway |
| FW-CORE (`em5`) | 10.10.53.1 | 00:0C:29:69:90:9E | VMnet7 | Substation Gateway |

(Detailed verification doc: [architecture/fw-core-mapping.md](file:///c:/Users/sterl/OneDrive/Desktop/GitHub/OT_ICS%20Project/ot-ics-lab-curriculum-package/ot-lab-curriculum/portfolio-repo/architecture/fw-core-mapping.md))

## Routing and emulation

- Single pfSense (FW-CORE) routes all zones; default-deny between them.
- Traffic limiters: 10 Mbps on site interfaces (WAN emulation). Measured effect: ___.
- Expansion path: split FW-IT / FW-OT — which rules move where (see FIREWALL-RULES.md §expansion).

## DNS and time

Windows → DC01. Linux/firewall → pfSense forwarder. NTP chain: ___.
Why time discipline matters here: (your one-paragraph answer — incident timelines depend on it)
