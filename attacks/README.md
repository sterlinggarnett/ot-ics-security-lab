# /attacks — Attack Exercise Folders

Each attack gets a folder using the template in `attacks/modbus-unauthorized-write/` (copy it, rename). Naming: `<technique-short-name>`.

## Index

| Attack | ATT&CK for ICS | Consequence | Report | Status |
|--------|----------------|-------------|--------|--------|
| A1 recon-port-scan | T0846.001 | none (recon) | | |
| A2 modbus-unauthorized-write | T1692.001 | tank overflow | | |
| A3 dnp3-command | T1692.001 | site state change | | |
| A4 hmi-brute-force | T0806 | account compromise | | |
| A5 plc-program-download | T0843 | logic modification | | |
| A6 plc-dos | T0814/T0815 | loss of view | | |
| A7 alarm-suppression | T0878 | silent overflow | | |
| A8 historian-tamper | T0832 | false history | | |
| A9 lateral-movement-it-ot | T0886/T0859 | full chain | | |
| A10 ransomware-simulation | T0809 | IT compromise + OT recovery | | |

## Per-folder evidence requirements

pcap/ (full-exercise capture), zeek/ (relevant log slices), suricata/ (alerts), screenshots/ (process consequence in HMI/Grafana), plus the six markdown files. Every attack ends with the target VM reverted to its pre-attack snapshot.
