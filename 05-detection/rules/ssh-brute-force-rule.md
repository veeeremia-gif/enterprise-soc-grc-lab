# SSH Brute-Force Detection Rule

## Rule Name

SSH Multiple Failed Authentication Attempts

## Objective

Detect repeated failed SSH password authentication attempts
from the same source IP address.

## Data Source

- Host: soc-01
- Service: OpenSSH
- Log source: `/var/log/auth.log`
- Event type: Failed password authentication

## Detection Condition

Trigger investigation when multiple SSH authentication
failure events are observed from the same source IP within
a short observation window.

## Relevant Fields

| Field | Description |
|---|---|
| timestamp | Time of authentication attempt |
| username | Targeted account |
| source_ip | Origin of authentication attempt |
| source_port | Source TCP port |
| protocol | SSH |
| authentication_result | Failed |

## Example Event

Failed password for ercvee from 127.0.0.1

## Threshold

Initial lab threshold:

5 failed authentication attempts from the same source IP
within a five-minute observation window.

## Severity

Medium

The severity is an initial laboratory classification and
should be validated against organizational context.

## Investigation

The analyst should determine:

1. Is the source IP expected?
2. Which account was targeted?
3. How many attempts occurred?
4. Over what time period?
5. Were successful authentications observed?
6. Was the activity local or remote?
7. Is there evidence of account compromise?
8. Are other systems affected?

## MITRE ATT&CK

Potential techniques:

- T1110 – Brute Force
- T1110.001 – Password Guessing

## Response Considerations

Depending on the investigation:

- Validate the source
- Review authentication history
- Review successful logins
- Verify account ownership
- Reset credentials if compromise is suspected
- Restrict the source if appropriate
- Enable stronger authentication
- Document the investigation

## SIEM Implementation / SIEM-Implementierung

### Deutsch

Die Detection wurde in Wazuh implementiert und validiert.

Wazuh Rule 5712 korreliert wiederholte fehlgeschlagene
SSH-Authentifizierungsversuche und erzeugt einen
Level-10-Alert.

Die Implementierung wurde in einer kontrollierten
Laborumgebung getestet.

### English

The detection was implemented and validated in Wazuh.

Wazuh Rule 5712 correlates repeated failed SSH authentication
attempts and generates a Level 10 alert.

The implementation was tested in a controlled laboratory
environment.

## Evidence / Nachweis

- Wazuh Rule: 5712
- Alert Level: 10
- MITRE ATT&CK: T1110 – Brute Force
- Alert evidence: `06-siem-wazuh/alerts/LAB-SSH-001-rule-5712.json`
- Analyst triage: `06-siem-wazuh/detections/LAB-SSH-001-triage.md`

## Status

**Validated in laboratory environment**
