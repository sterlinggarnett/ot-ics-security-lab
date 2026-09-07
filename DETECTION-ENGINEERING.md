# DETECTION ENGINEERING — Garnett Water & Power

Methodology summary + index. Individual detections live in /detections/D1…D9. Method: define → justify → generate → capture → write → test → tune → document.

## Index

| ID | Detection | Layer | Philosophy | Status |
|----|-----------|-------|-----------|--------|
| D1 | Modbus write from unauthorized source | Suricata | known-malicious | |
| D2 | New Modbus master | Zeek | known-abnormal | |
| D3 | Unexpected PLC communication pattern | Zeek | known-abnormal | |
| D4 | Unauthorized program download / online edit | Suricata + app log | known-malicious | |
| D5 | Unusual RDP path | Windows/Sysmon | known-malicious | |
| D6 | Authentication anomaly | Windows events | known-malicious | |
| D7 | Suspicious lateral movement correlation | Sysmon | known-malicious | |
| D8 | Abnormal process value | Grafana | known-abnormal | |
| D9 | Historian integrity | FIM/audit | known-malicious | |

## Coverage vs. attack set

| Attack | Detections that fired | Gap analysis |
|--------|----------------------|--------------|
| A1–A10 | | |

## False-positive log

| Date | Detection | False positive cause | Tuning action |
|------|-----------|---------------------|---------------|
| | | | |

## What I learned engineering these

(Your honest retrospective — which detection was hardest and why, what surprised you, what you'd deploy differently with real hardware.)
