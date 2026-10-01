# Wazuh SIEM Installation & Validation

## Objective / Ziel

### Deutsch

Bereitstellung und Validierung von Wazuh als zentrale SIEM-Plattform innerhalb des Enterprise SOC/GRC Labors.

### English

Deploy and validate Wazuh as the central SIEM platform within the Enterprise SOC/GRC laboratory.

---

## Host / System

| Field / Feld | Value / Wert |
|---|---|
| Hostname | SOC-01 |
| Operating System | Ubuntu 24.04.5 LTS |
| CPU | 4 vCPU |
| RAM | 8 GB |
| Disk | 80 GB |
| Network | 192.168.220.0/24 |
| SOC/Wazuh Manager IP | 192.168.220.129 |

---

## Wazuh Components / Wazuh-Komponenten

The Wazuh platform consists of the following validated components:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- Filebeat

All four components were confirmed active during the documented health check.

---

## Platform Role / Funktion der Plattform

Wazuh is used in this laboratory for:

- Security monitoring
- Centralized log collection
- Detection and alert generation
- Authentication monitoring
- File integrity monitoring
- Vulnerability detection
- MITRE ATT&CK mapping
- Security investigation
- GRC evidence generation

---

## Initial Log Sources / Erste Logquellen

The laboratory initially monitors:

- Linux authentication logs
- SSH authentication events
- System logs

---

## Validation / Validierung

The Wazuh platform was successfully validated through:

- Service health verification
- Network connectivity verification
- Listening port verification
- SSH authentication event collection
- Wazuh Rule 5712 detection
- Level 10 alert generation
- Analyst triage

The documented SSH detection case is:

**LAB-SSH-001 – SSH Brute-Force Detection Validation**

---

## Detection Validation / Erkennungsvalidierung

Wazuh successfully detected repeated SSH authentication attempts against the non-existent user `fakeuser`.

The activity triggered:

- Wazuh Rule: 5712
- Wazuh Level: 10
- MITRE ATT&CK: T1110 – Brute Force

The detection was generated as part of an authorized laboratory simulation.

---

## Planned Integrations / Geplante Integrationen

The following integrations are planned for future laboratory phases:

- Sigma detection rules
- Suricata IDS
- Zeek network monitoring
- MITRE ATT&CK enrichment
- NIST CSF
- Incident Response workflows
- GRC risk analysis

---

## Status / Status

**Installation:** Completed

**Core Services:** Validated

**Log Collection:** Validated

**Detection:** Validated

**Analyst Triage:** Validated

**GRC Mapping:** Completed

**Future Integrations:** Planned

---

## Evidence Reference / Evidenzreferenz

Health check evidence:

`06-siem-wazuh/evidence/health-check/wazuh-health-check.txt`

Detection case:

`06-siem-wazuh/detections/LAB-SSH-001.md`

Analyst triage:

`06-siem-wazuh/detections/LAB-SSH-001-triage.md`

GRC risk register:

`07-grc-risk-management/risk-register.md`

NIST CSF mapping:

`07-grc-risk-management/nist-csf-mapping.md`
