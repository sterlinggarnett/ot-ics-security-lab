# Detection Analysis — A2 Unauthorized Modbus Write

## What fired

| Layer | Detector | Fired? | Time delta from first packet | Evidence file |
|-------|----------|--------|------------------------------|---------------|
| Firewall | pfSense deny (if source unreachable through a zone) | | | |
| IDS | Suricata D1 (write FC from unauthorized source) | | | |
| Metadata | Zeek D2 (new Modbus master) | | | |
| Baseline | Zeek D3 (unexpected pattern) | | | |
| Process | Grafana D8 (rate-of-change) | | | |
| Human | Operator notices tank in FUXA | | | |

## Gap analysis

For every layer that did NOT fire: why not? Missing rule? Rule disabled? Detection logic error? Tuning too aggressive? This section is the actual learning.

## Detection latency

first malicious packet → first alert: ___ (track this across exercises; improving it is the job)
