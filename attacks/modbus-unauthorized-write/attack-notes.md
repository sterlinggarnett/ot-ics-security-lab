# Attack Notes — A2 Unauthorized Modbus Write

## Prediction (BEFORE executing — gate)

- Predicted packet signature of the attack: ___
- Predicted first detector to fire: ___
- Predicted process consequence and time-to-consequence: ___
- Predicted evidence in each layer (firewall / Suricata / Zeek / Grafana / HMI): ___

## Execution

- Date/time window (UTC): ___
- Source: KALI-01 attached to VLAN ___
- Technique: pymodbus write to holding register ___ (value ___) — target: pump output / valve
- Every command used, in order (with notes on what each did)

## Observation

- Time of first malicious packet: ___
- Time of first process change visible in Grafana: ___
- Time of first alarm in FUXA: ___
- Time of first alert in any detector: ___
- Build the timeline; note the deltas (detection latency is a metric — track it)

## The eight questions

1. Who communicated? 2. With whom? 3. When? 4. Using what protocol? 5. What command? 6. Normal, abnormal, or malicious vs. baseline? 7. What changed? 8. Operational consequence?
