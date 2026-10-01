# Risk Register – LAB-SSH-001

## Risk ID

RISK-SSH-001

## Related Security Case

LAB-SSH-001 – SSH Brute-Force Detection Validation

---
## Risk Statement
Repeated SSH authentication attempts could lead to unauthorized access to the server if valid credentials were successfully compromised.

## Threat
Brute-force attacks targeting the SSH authentication service.
---

## Potential Vulnerability

An SSH service can be targeted by repeated authentication attempts. The risk may increase when weak or compromised credentials are used or when additional access controls are missing.

---

## Potential Impact

Successful unauthorized access to the server could potentially result in:

- Unauthorized access to systems and data
- Account misuse
- Privilege escalation
- Modification of systems or files
- Service disruption
- Potential data loss or data exfiltration

---

## Security Objectives

The relevant security objectives are:

- Confidentiality
- Integrity
- Availability
---

## Risk Assessment

### Likelihood

**Rating:** Medium

Repeated SSH authentication attempts can occur in real-world environments. The likelihood of successful access depends on factors such as credential strength, MFA, network exposure, and existing access controls.

### Impact

**Rating:** High

Successful unauthorized access to the server could potentially affect confidentiality, integrity, and availability.

### Overall Risk

**Rating:** High

**Risk Basis:** Medium Likelihood × High Impact

---

## Risk Treatment

**Treatment:** Mitigate

The risk should be reduced through preventive, detective, and access-control measures.

### Recommended Controls

- Use strong authentication mechanisms and SSH keys where appropriate.
- Restrict SSH access to authorized management networks or hosts where feasible.
- Consider MFA for privileged or sensitive access.
- Continue centralized monitoring through Wazuh.
- Monitor repeated authentication failures and brute-force patterns.
- Apply least-privilege principles to accounts with server access.

---

## Residual Risk

Residual risk may remain after additional controls are implemented. Control effectiveness should be reviewed periodically and supported by continuous security monitoring.

---

## Risk Owner

**Role:** System / Infrastructure Owner

---

## Review Status

**Status:** Open – Risk Treatment Recommended

---

## Evidence Reference

- LAB-SSH-001 detection case
- Wazuh Rule 5712
- Wazuh Level 10
- Source IP: 192.168.220.129
- Target IP: 192.168.220.130
- Username: fakeuser
- MITRE ATT&CK T1110 – Brute Force
