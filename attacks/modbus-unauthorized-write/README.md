# Attack A2 — Unauthorized Modbus Write

**ATT&CK for ICS:** T1692.001 Unauthorized Message: Command Message (legacy T0855) · Tactic: Impair Process Control
**Target:** Water Plant PLC (10.10.51.10:502) · **Operational consequence:** tank overflow

## Summary (fill after the exercise)

One paragraph: what was attacked, what the consequence was, what detected it.

## Chain demonstrated

attack (Modbus write FC from unauthorized source) → control change (pump output / valve) → process change (level rise beyond envelope) → consequence (overflow alarm / high-high) → detection (which layers fired?) → response → recovery

## Contents

- attack-notes.md — planning, prediction, execution
- pcap/ — full capture
- zeek/ — log slices (conn.log, modbus.log)
- suricata/ — alerts (or "none fired — gap analysis")
- screenshots/ — HMI/Grafana during the overflow, IDS alerts
- detection.md — what fired, what didn't, gap analysis
- mitre.md — technique mapping with rationale
- incident-report.md — full IR cycle (Stage 9)
- mitigation.md — controls added afterward
- lessons-learned.md — the honest part
