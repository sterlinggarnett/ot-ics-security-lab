# Garnett Water & Power — OT/ICS Security Laboratory

A portfolio project: a simulated utility (corporate IT, OT DMZ, central operations, three remote sites) built and defended in VMware Workstation on student hardware. The lab demonstrates the full OT security engineering cycle:

**attack → control system change → process change → operational consequence → network evidence → detection → investigation → containment → recovery → hardening**

## Architecture

![Architecture](diagrams/architecture.png)

Purdue-model zones: Corporate (L5/4) → OT DMZ with jump host (L3.5) → Central OT: SCADA, engineering workstation, sensor (L3) → Water / Pipeline / Substation sites with OpenPLC, FUXA HMI, DNP3 outstation, process simulators (L2/1/0). All inter-zone traffic crosses a pfSense firewall with default-deny policy.

## What's in this repo

| Path | Contents |
|------|----------|
| [ARCHITECTURE.md](ARCHITECTURE.md) | Zones, Purdue levels, trust boundaries, component rationale |
| [NETWORK.md](NETWORK.md) | VMnets, VLANs, IP plan, WAN emulation |
| [FIREWALL-RULES.md](FIREWALL-RULES.md) | Every rule with its justification (rule ledger) |
| [ASSET-INVENTORY.md](ASSET-INVENTORY.md) | Every asset: IP, Purdue level, protocols, criticality, controls |
| [OT-BASELINE.md](OT-BASELINE.md) | Normal traffic: peers, ports, protocols, frequencies |
| [DETECTION-ENGINEERING.md](DETECTION-ENGINEERING.md) | Nine custom detections: methodology and results |
| [INCIDENT-RESPONSE.md](INCIDENT-RESPONSE.md) | OT IR process + incident reports index |
| [RECOVERY.md](RECOVERY.md) | Backup taxonomy, matrix, restoration testing |
| [LESSONS-LEARNED.md](LESSONS-LEARNED.md) | What broke, what surprised me, what I'd change |
| /attacks/ | One folder per attack: evidence, MITRE mapping, report, mitigation |
| /detections/ | The rules themselves + test evidence |
| /pcaps/ | Baseline and exercise captures |
| /process-models/ | Water / pipeline / substation simulator designs |
| /lab-notes/ | Build journal: predictions before, explanations after |

## Featured

- **Flagship incident report:** [incident-response/2026-xx-plc-program-modification.md](incident-response/) — full chain from first packet to recovery
- **Best detection:** [detections/D2-new-modbus-master.md](detections/) — baseline anomaly detection
- **Defense-in-depth matrix:** [hardening/layer-failure-matrix.md](hardening/)

## Tools

OpenPLC, FUXA, Ignition Maker Edition, InfluxDB/Grafana/Telegraf, pfSense, Zeek, Suricata, Wazuh, Windows Server 2022 eval AD, Sysmon/WEF, Kali. All open-source or free evaluation licenses.

## Scope note

All attacks were executed against systems I own, inside isolated lab networks. This repository documents defensive security research and education.
