# MITRE ATT&CK for ICS Mapping — A2 Unauthorized Modbus Write

## Techniques

| Technique | ID | How this attack implements it |
|-----------|-----|-------------------------------|
| Unauthorized Message: Command Message | T1692.001 | The attack's core: a command message (Modbus write) instructing a control asset outside its intended use |

## Why this mapping is correct (the required paragraph)

(In your own words: what makes this a Command Message technique rather than, say, Modify Parameter (T0836) or Manipulate I/O Image (T0835)? Consider: did you change a setpoint (parameter), write the I/O image directly, or issue a command outside intended functionality? If your variant actually fits a different technique better, SAY SO and justify it — wrong-but-argued beats right-but-copied.)

## Related real-world procedures

From the ATT&CK page (attack.mitre.org/techniques/T1692/): which known malware/incidents used this technique (e.g., INCONTROLLER's custom Modbus commands, Industroyer's RTU commands)? One sentence each on how yours differs.

## Kill-chain position

Where in the chain did this attack enter? (Note: A2 assumes you're already inside the site VLAN — the full chain including entry is A9.)
