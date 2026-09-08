# Lab notes — predictions (HARD GATE journal)

> RULE: every entry is written BEFORE reading the implementation steps. Never edit after the fact — add corrections below the entry instead.

## Format

```
### <date> — <stage.task> — <short name>
PREDICTION:
- What I expect to happen: ...
- Why: ...
CORRECTION (after the build):
- What actually happened: ...
- What I misunderstood: ...
```

2026-09-07 — Stage 0.1 — VMware VMnets & Purdue Model Foundations

PREDICTION:
- What I expect to happen: Set up Host-Only VMnets according to the IP plan in NETWORK.md.
- Why: To establish the virtual network adapters needed to simulate Purdue Model network isolation.

CORRECTION & LESSONS LEARNED (after the build):
- What actually happened: Cleared out old legacy lab VMnets in VMware. Configured VMnets 2–7 for host-only isolation and disabled VMware DHCP on all OT subnets so pfSense acts as the sole router and gateway.
- What I misunderstood: I originally thought the Purdue Model was primarily a organizational framework for sorting devices. I learned that it is a strict security architecture designed to enforce trust boundaries—forcing even internal corporate-to-OT traffic through DMZ jump hosts, firewalls, and IDS/SIEM sensors to protect PLCs, RTUs, and HMIs from internal and external threats.
