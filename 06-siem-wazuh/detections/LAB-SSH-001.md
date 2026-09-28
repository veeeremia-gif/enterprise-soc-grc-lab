# LAB-SSH-001 – SSH Brute-Force Detection Validation

## Status
Closed – Controlled Lab Simulation

## Date
2026-09-28

## Objective
Validate that Wazuh detects repeated SSH authentication attempts against a non-existent user.

## Environment
- SOC-01: 192.168.220.129
- SRV-01: 192.168.220.130
- Wazuh Manager: SOC-01
- Wazuh Agent: SRV-01

## Detection
- Rule ID: 5712
- Wazuh Level: 10
- Description: sshd brute force attempt using a non-existent user
- Source IP: 192.168.220.129
- Target: SRV-01
- Username: fakeuser
- Frequency: 8

## MITRE ATT&CK
- Technique: T1110 – Brute Force
- Tactic: Credential Access

## Result
Wazuh successfully correlated repeated failed SSH authentication attempts and generated a Level 10 alert.

## Context
The activity was intentionally generated from SOC-01 as an authorized laboratory simulation. No compromise occurred.

## Evidence
- Wazuh Rule 5712 alert
- Source IP 192.168.220.129
- Target IP 192.168.220.130
- Repeated failed SSH authentication attempts

## Analyst Conclusion
Detection was successful. The event represents a validated security monitoring use case, not a real-world compromise.

## Timeline

- 11:14:41 – First invalid SSH user attempt observed.
- 11:14:49 – Repeated failed SSH authentication attempts observed.
- 11:15:02 – Wazuh Rule 5712 triggered.
- 11:15:02 – Wazuh Level 10 alert generated.

## Response

- Activity confirmed as an authorized laboratory simulation.
- Source host: SOC-01 (192.168.220.129).
- Target host: SRV-01 (192.168.220.130).
- No containment required because the activity was intentionally generated for detection validation.
- Wazuh alert evidence preserved in the repository.

## Lessons Learned

- Confirmed end-to-end log collection from SRV-01 to SOC-01.
- Confirmed SSH event decoding and rule correlation in Wazuh.
- Confirmed MITRE ATT&CK T1110 mapping.
- Demonstrated the difference between a security alert and a confirmed incident.
