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

---

### 2026-09-07 — Stage 0.1 — VMware VMnets & Purdue Model Foundations

PREDICTION:
- What I expect to happen: Set up Host-Only VMnets according to the IP plan in NETWORK.md.
- Why: To establish the virtual network adapters needed to simulate Purdue Model network isolation.

CORRECTION & LESSONS LEARNED (after the build):
- What actually happened: Cleared out old legacy lab VMnets in VMware. Configured VMnets 2–7 for host-only isolation and disabled VMware DHCP on all OT subnets so pfSense acts as the sole router and gateway.
- What I misunderstood: I originally thought the Purdue Model was primarily an organizational framework for sorting devices. I learned that it is a strict security architecture designed to enforce trust boundaries—forcing even internal corporate-to-OT traffic through DMZ jump hosts, firewalls, and IDS/SIEM sensors to protect PLCs, RTUs, and HMIs from internal and external threats.

---

### 2026-09-08 — Stage 1.1 — FW-CORE VMnets & Interface Setup

PREDICTION:
- What I expect to happen: Configure the VMnets in VMware and work with pfSense to prepare for the next steps.
- Why: Because I need six separate networks in VMware to build the segmented network architecture for my Purdue Model lab.

CORRECTION & LESSONS LEARNED (after the build):
- What actually happened: I created the six VMnets, added the virtual network adapters in VMware, and mapped each adapter to pfSense using its MAC address. It took some time to make sure every interface was connected to the correct VMnet, but I got them all connected.
- What I misunderstood: I originally thought I would use one VMnet and create the VLANs from there. Instead, each network has its own isolated VMnet. The OT networks use host-only networking with VMware DHCP disabled, allowing pfSense to control routing and keeping addressing predictable so traffic cannot bypass the firewall.
