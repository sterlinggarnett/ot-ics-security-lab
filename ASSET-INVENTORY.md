# ASSET INVENTORY — Garnett Water & Power

> You cannot defend what you don't know exists. Complete by end of Stage 6; audit every stage after.
> Container-level assets (PLC, HMI, RTU per site) get their own rows — they are separate devices to the network.

| Asset | IP | MAC | Hostname | Purdue Level | Zone | Function | OS/Platform | Protocols | Criticality | Owner (role) | Expected communications | Security controls |
|-------|-----|-----|----------|--------------|------|----------|-------------|-----------|-------------|--------------|-------------------------|-------------------|
| FW-CORE | 10.10.x.1 (all) | | | 3.5/3 boundary | all | Firewall/router | pfSense CE | — | CRITICAL | SecEng | routes all zones | default-deny, logging |
| DC01 | 10.10.10.10 | | | 5 | Corporate | AD/DNS/DHCP/GPO | Win Server 2022 | AD (Kerberos, LDAP, SMB, DNS) | HIGH | IT | Corporate clients | GPO hardening, WEF |
| | | | | | | | | | | | | |

**Criticality scale:** CRITICAL (process stops if lost) / HIGH (degraded operation) / MEDIUM (supporting) / LOW.

**How to fill MACs:** Zeek's `dhcp.log`/`conn.log`, `arp`, or `docker inspect` — this inventory is also a Zeek exercise: can you build it purely from network observations? (That's how passive OT asset discovery works — compare your result with the ground truth.)

## Notes

- Expected communications column should match OT-BASELINE.md exactly. If they drift, one of them is wrong — investigate.
- Update this inventory after every hardening change and every new container.
