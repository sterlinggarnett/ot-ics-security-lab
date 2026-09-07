# OT NETWORK BASELINE — Garnett Water & Power

> Produced in Stage 5 (v1) and Stage 6 (v2) from 48+ hours of untouched operation.
> This document IS a security control: every "known abnormal" detection in DETECTION-ENGINEERING.md is a diff against this baseline.

## Method

Capture window: ___ to ___ . Sources: Zeek conn.log / modbus.log / dnp3.log, pfSense logs, Grafana process trends, PCAP spot checks.

## Network baseline — per asset

| Asset | Normal peers | Ports | Protocols | Direction | Frequency | Notes |
|-------|--------------|-------|-----------|-----------|-----------|-------|
| SCADA-CENT | SITE1 .10/.12 | 502, 20000 | Modbus, DNP3 | outbound | ~1/sec | polling |
| | | | | | | |

## Protocol behavior baseline

**Modbus:** who issues reads? ___ Who issues writes? ___ Which function codes appear in normal operation? ___ Which registers get written, by whom, how often? ___
**DNP3:** which object groups/variants appear? ___ Unsolicited responses? ___
**OPC UA:** sessions, subscriptions, read/write split? ___
**RDP:** the two legal session paths? ___ Normal hours? ___

## Process baseline (per site)

- Water: normal fill/drain cycle shape, level envelope, max rate-of-change ___
- Pipeline: normal pressure envelope, ESD never active ___
- Substation: frequency band, breaker states ___

## Vocabulary (write your own examples)

- **Known good:** (e.g., SCADA→PLC polling at 1 Hz)
- **Known abnormal:** (e.g., new source issuing Modbus reads)
- **Unknown:** (e.g., traffic you can't classify — investigate until it moves up or down)
- **Known malicious:** (e.g., Modbus write FC from Kali — but note: on day one, it's only "abnormal" — the malicious label comes from context)

## Version history

| Version | Date | Scope | Change |
|---------|------|-------|--------|
| 1 | | Central OT + Water site | initial |
