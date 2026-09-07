# INCIDENT RESPONSE — Garnett Water & Power

OT-adapted PICERL process + incident report index. Reports live in /incident-response/. Full playbook (IT vs OT differences, evidence handling, templates) is in the build handbooks.

## The process (one screen)

1. **Preparation** — backups tested, detections live, runbook current, contacts/roles defined (in this lab: you are all roles; document the hats).
2. **Detection** — alert fires (or operator reports process anomaly).
3. **Identification** — scope: which assets, which zones, active or historic? Preserve evidence FIRST.
4. **Containment** — OT-appropriate: can you isolate the PLC without tripping the process? Fail-safe first.
5. **Eradication** — remove access + malicious changes (program downloads, credentials, rules).
6. **Recovery** — restore from trusted backups, verify against independent sources (second historian).
7. **Lessons learned** — the report; every fix becomes a hardening change with a motivating incident.

## The OT difference (my one-paragraph answer)

(Rrompt: in IT, "disconnect the machine." In OT, disconnecting may stop a physical process — write your own statement of the trade-off, safety vs availability vs integrity, and who decides. Cite your A5 decision as the example.)

## Incident reports

| ID | Date | Type | ATT&CK for ICS | Severity | Report |
|----|------|------|----------------|----------|--------|
| IR-01 | | Unauthorized Modbus write (A2) | T1692.001 | HIGH | [modbus-write report]() |
| IR-02 | | PLC program modification (A5) | T0843 | CRITICAL | |
| IR-03 | | Lateral movement IT→OT (A9) | T0886/T0859 | CRITICAL | |

## Evidence handling rules (this lab)

PCAP before reboot. Snapshot before cleanup. Never analyze on the compromised host. Timeline in UTC + lab-local, both stated.
