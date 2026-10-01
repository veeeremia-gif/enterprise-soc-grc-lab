# NIST CSF Mapping – LAB-SSH-001

## Overview / Überblick

### Deutsch

Dieses Dokument ordnet den Security-Monitoring-Fall LAB-SSH-001 den Funktionen des NIST Cybersecurity Framework (CSF) zu.

Der Fall demonstriert die Erkennung und Untersuchung wiederholter SSH-Authentifizierungsversuche gegen einen nicht existierenden Benutzer.

### English

This document maps the security monitoring case LAB-SSH-001 to the functions of the NIST Cybersecurity Framework (CSF).

The case demonstrates the detection and investigation of repeated SSH authentication attempts against a non-existent user.

---

# 1. Identify

## Objective / Ziel

### Deutsch

Identifizierung der betroffenen Systeme, des Sicherheitsrisikos und des relevanten Security Use Cases.

### English

Identification of the affected systems, security risk, and relevant security use case.

## Lab Evidence / Lab-Nachweis

- SOC-01 identified as the Wazuh Manager.
- SRV-01 identified as the monitored target.
- SSH authentication identified as the monitored service.
- Risk RISK-SSH-001 documented in the Risk Register.

## GRC Relevance / GRC-Relevanz

The activity was translated into a documented security risk and linked to the affected asset and security monitoring use case.

---

# 2. Protect

## Objective / Ziel

### Deutsch

Reduzierung des Risikos eines erfolgreichen unbefugten Zugriffs durch präventive Sicherheitskontrollen.

### English

Reduce the risk of successful unauthorized access through preventive security controls.

## Recommended Controls / Empfohlene Kontrollen

- Use strong authentication mechanisms.
- Use SSH key-based authentication where appropriate.
- Restrict SSH access to authorized management networks or hosts where feasible.
- Consider MFA for privileged or sensitive access.
- Apply least-privilege principles.

## Status

**Recommended – Not fully validated in this lab**

---

# 3. Detect

## Objective / Ziel

### Deutsch

Erkennung verdächtiger SSH-Authentifizierungsaktivitäten.

### English

Detect suspicious SSH authentication activity.

## Lab Evidence / Lab-Nachweis

- Wazuh Manager: SOC-01
- Wazuh Agent: SRV-01
- Wazuh Rule: 5712
- Wazuh Level: 10
- Source IP: 192.168.220.129
- Target IP: 192.168.220.130
- Username: fakeuser
- MITRE ATT&CK: T1110 – Brute Force

## Validation Result / Validierungsergebnis

Wazuh successfully detected and correlated repeated failed SSH authentication attempts and generated a Level 10 alert.

## Status

**Validated in laboratory environment**

---

# 4. Respond

## Objective / Ziel

### Deutsch

Untersuchung des Alerts, Bewertung der Aktivität und Entscheidung über erforderliche Reaktionsmaßnahmen.

### English

Investigate the alert, assess the activity, and determine the appropriate response.

## Lab Evidence / Lab-Nachweis

- Analyst triage performed.
- Authentication events reviewed.
- Source and target systems identified.
- No successful authentication observed in the reviewed Wazuh alerts.
- Activity confirmed as an authorized laboratory simulation.
- No containment action required.

## Status

**Validated in laboratory environment**

---

# 5. Recover

## Objective / Ziel

### Deutsch

Verbesserung der Sicherheitskontrollen und Dokumentation der gewonnenen Erkenntnisse nach der Untersuchung.

### English

Improve security controls and document lessons learned following the investigation.

## Lessons Learned / Erkenntnisse

- SSH authentication logging was successfully collected.
- Wazuh detection and correlation were validated.
- Analyst triage procedures were documented.
- MITRE ATT&CK T1110 mapping was validated.
- Risk RISK-SSH-001 was documented.
- Additional preventive controls were identified.

## Recommended Improvements / Empfohlene Verbesserungen

- Review SSH exposure and access restrictions.
- Review authentication controls.
- Continue centralized security monitoring.
- Periodically review detection effectiveness.
- Review and update the associated risk assessment.

## Status

**Improvement actions identified**

---

# NIST CSF Summary / Zusammenfassung

| Function | Lab Status | Evidence |
|---|---|---|
| Identify | Documented | Asset and risk identification |
| Protect | Recommended | Authentication and access controls |
| Detect | Validated | Wazuh Rule 5712 |
| Respond | Validated | Analyst triage |
| Recover | Improvement actions identified | Lessons learned and risk treatment |

---

## Case Reference

**Security Case:** LAB-SSH-001

**Risk:** RISK-SSH-001

**Detection:** Wazuh Rule 5712

**MITRE ATT&CK:** T1110 – Brute Force

**Case Status:** Closed – Controlled Lab Simulation
