# FIREWALL RULES — Garnett Water & Power

Every rule that exists, why it exists, and when it was added. The complete matrix with doctrine lives in the build handbooks; this is the living ledger for THIS lab instance.

## Standing policy

Default: DENY ALL between zones. Every ALLOW below is a conscious, justified, logged exception. Rule O-12 (Corporate → any OT zone) must never exist and is re-verified every stage.

## Enterprise boundary

| Rule ID | Source | Dest | Proto:Port | Purpose | Verdict | Log | Added (stage) |
|---------|--------|------|-----------|---------|---------|-----|---------------|
| E-01 | | | | | | | |
| E-02 | | | | | | | |

## OT DMZ boundary

| Rule ID | Source | Dest | Proto:Port | Purpose | Verdict | Log | Added (stage) |
|---------|--------|------|-----------|---------|---------|-----|---------------|
| D-01 | | | | | | | |

## OT boundary

| Rule ID | Source | Dest | Proto:Port | Purpose | Verdict | Log | Added (stage) |
|---------|--------|------|-----------|---------|---------|-----|---------------|
| O-01 | | | | | | | |
| O-02 | EWS-01 → DC01 | | AD/DNS/Kerberos/LDAP/SMB/RPC | **Documented lab compromise** — see FIREWALL handbook §3 for the risk and the production alternatives (RODC / one-way trust / separate OT domain) | | | |

## Change log

| Date | Rule | Change | Motivating incident/exercise |
|------|------|--------|-------------------------------|
| | | | |

## Expansion plan (single firewall → FW-IT + FW-OT)

Which rules move to which future firewall, and what the hardest rule (D-03 jump host → AD) becomes.
