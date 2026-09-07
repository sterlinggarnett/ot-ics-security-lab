# RECOVERY — Garnett Water & Power

Backup taxonomy, per-asset matrix, restoration testing log. Full playbook and the guided destruction scenario live in the build handbooks (Stage 10).

## The five kinds of "backup" (my definitions, in my words)

| Type | What it protects | What it does NOT protect | When it's the right tool |
|------|------------------|--------------------------|---------------------------|
| VM snapshot | | | |
| System backup (image) | | | |
| Configuration backup | | | |
| PLC program backup | | | |
| Data backup (historian) | | | |

(Write these yourself in Stage 10 — if you can't fill the "does NOT protect" column, you don't understand the type yet.)

## Backup matrix

| Asset | What | How | Schedule | Restore tested (date) | Notes |
|-------|------|-----|----------|----------------------|-------|
| FW-CORE | config.xml | Diagnostics → Backup & Restore | after every rule change | | |
| DC01 | System State + GPO backups | | | | |
| EWS-01 / JUMP-01 / CORP-PC | | | | | |
| OpenPLC (each site) | program export (.st/.xml) + register map | | | | |
| FUXA | project JSON | | | | |
| Ignition | gateway backup (.gwbk) | | | | |
| SCADA-CENT | compose files + volumes | | | | |
| InfluxDB | bucket snapshots | | | | |
| SENSOR-01 | Zeek/Suricata configs + custom rules | | | | |

**Untested backup = decorative backup.** A restore isn't "done" until the service is verified working AND its data matches the independent historian.

## Restoration test log

| Date | Asset | Restored from | Verification | Gaps found |
|------|-------|---------------|--------------|------------|
| | | | | |

## The destruction scenario (Stage 10 walkthrough)

PLC program modified + historian day deleted: detection → containment decision (documented trade-off) → program restore → register map verification → historian restore → cross-validation against PostgreSQL historian → residual gaps. Full narrative in reports/.
