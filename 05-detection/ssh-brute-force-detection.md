# SSH Brute-Force Detection

## Objective

Detect repeated failed SSH authentication attempts that may indicate
password guessing or brute-force activity.

## Log Source

- Host: soc-01
- Operating System: Ubuntu 24.04.5 LTS
- Service: OpenSSH
- Log Source: `/var/log/auth.log`

## Detection Logic

The detection looks for repeated events containing:

`Failed password`

The source IP address is extracted and authentication failures
are grouped by source.


### Parsing Approach

The initial parsing approach used a fixed field position with `awk`.
This produced false matches because `sudo` audit entries also contained
the string `Failed password`.

The detection was refined to:

1. Filter for `sshd` events.
2. Search for `Failed password`.
3. Extract the source IP from the `from <IP>` field.
4. Aggregate authentication failures by source IP.

This reduces false matches from administrative commands that reference
the same search term.

## Investigation Questions

When repeated failures are detected, the analyst should determine:

1. Which source IP generated the attempts?
2. Which username was targeted?
3. How many failures occurred?
4. Over what time period?
5. Was a successful authentication observed afterwards?
6. Is the source expected or suspicious?
7. Does the event require containment?

## Lab Observation

The current lab generated failed SSH authentication events from:

`127.0.0.1`

This is expected because the authentication tests were performed
locally on the SOC host.

Therefore, the observed activity is a controlled lab simulation
and not evidence of an external attack.

## Potential SOC Response

If the source were confirmed as malicious, possible response actions
could include:

- Investigate the source IP
- Review successful authentications
- Verify the targeted account
- Reset credentials if compromise is suspected
- Restrict or block the source
- Enable stronger authentication such as SSH keys
- Review related authentication logs
- Escalate according to the incident response process

## MITRE ATT&CK Mapping

Potential technique:

- T1110 – Brute Force
- T1110.001 – Password Guessing

## SIEM Implementation / SIEM-Implementierung

### Deutsch

Die Detection wurde in Wazuh implementiert und erfolgreich validiert.

Wazuh erkannte wiederholte fehlgeschlagene SSH-Authentifizierungsversuche
und erzeugte einen Level-10-Alert unter Verwendung von Wazuh Rule 5712.

Die Detection wurde in einer kontrollierten Laborumgebung getestet.

### English

The detection was implemented and successfully validated using Wazuh.

Wazuh detected repeated failed SSH authentication attempts and generated
a Level 10 alert using Wazuh Rule 5712.

The detection was tested in a controlled laboratory environment.

### Validation Evidence / Validierungsnachweis

- Wazuh Rule: 5712
- Alert Level: 10
- MITRE ATT&CK: T1110 – Brute Force
- Alert evidence: `06-siem-wazuh/alerts/LAB-SSH-001-rule-5712.json`
- Detection case: `06-siem-wazuh/detections/LAB-SSH-001.md`
- Analyst triage: `06-siem-wazuh/detections/LAB-SSH-001-triage.md`

### Status

**Validated in laboratory environment**
