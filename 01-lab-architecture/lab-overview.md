# Cybersecurity Lab Overview

## Project

Enterprise SOC & GRC Cybersecurity Lab

## Objective

The objective of this project is to build a realistic,
isolated cybersecurity laboratory that combines technical
Security Operations Center capabilities with Governance,
Risk and Compliance practices.

The laboratory will simulate an enterprise environment
where security events can be generated, detected,
investigated and translated into business risks and
security controls.

## Security Lifecycle

The laboratory follows the following lifecycle:

1. Asset Identification
2. Threat Analysis
3. Attack Simulation
4. Security Monitoring
5. Detection
6. SOC Investigation
7. Incident Response
8. Risk Assessment
9. Risk Treatment
10. Security Controls
11. NIST CSF Mapping
12. Management Reporting

## Infrastructure

The environment is built using VMware virtual machines
and an isolated Host-only network.

### Planned Systems

| Host | IP | Role |
|---|---|---|
| SOC-01 | 192.168.100.10 | SOC / SIEM |
| SRV-01 | 192.168.100.20 | Business Server |
| ATTACK-01 | 192.168.100.30 | Security Testing |

## Planned Security Technologies

### SIEM

- Wazuh
- Splunk

### Network Security

- Wireshark
- Zeek
- Suricata

### Vulnerability Management

- Greenbone / OpenVAS
- Nmap

### Host Security

- Linux auditd
- Fail2ban
- SSH hardening
- Linux firewall

### Automation

- Python
- SQL

## GRC

The technical findings will be connected to:

- Asset Management
- Risk Assessment
- Risk Register
- Risk Treatment
- Security Controls
- NIST Cybersecurity Framework
- Management Reporting

## Documentation

All significant implementation steps, configuration
changes, tests, evidence and security findings will be
documented in this repository.

Selected project milestones will also be documented publicly
on LinkedIn.

## Security Scope

All security testing is performed exclusively against
systems created for this laboratory.

No production systems or third-party systems are targeted.
