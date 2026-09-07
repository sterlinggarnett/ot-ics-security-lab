# Mitigation — A2 Unauthorized Modbus Write

Every control added or changed because of this exercise. Each entry must cite the motivating evidence.

## Network

- Firewall rule(s) tightened (cite rule ID in FIREWALL-RULES.md): ___
- Verified: re-ran the attack, packet died at ___ with log entry ___

## Detection

- New/tuned detection(s) (cite D-ID in DETECTION-ENGINEERING.md): ___
- Verified: replay fires, 24h normal ops quiet

## Process/endpoint

- PLC register-write allowlisting, ufw changes, GPO changes: ___

## Residual risk

What this mitigation does NOT cover (be honest — e.g., "D1 stops unauthorized writes from known segments; a compromised SCADA-CENT still writes legitimately").
