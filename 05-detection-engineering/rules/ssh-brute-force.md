# SSH Brute-Force Detection

## Detection ID

DET-SSH-001

## Name

Multiple Failed SSH Authentication Attempts

## Objective

Detect repeated failed SSH authentication attempts that may indicate
password guessing or brute-force activity.

## Log Source

- Host: soc-01
- Service: OpenSSH
- Log source: /var/log/auth.log
- Event type: Failed password

## Detection Logic

Trigger an alert when multiple failed SSH authentication attempts
occur for the same account or from the same source IP within a
short time window.

## Example Event

Failed password for ercvee from 127.0.0.1

## Relevant Fields

- timestamp
- username
- source_ip
- source_port
- authentication_method
- host
- process

## Investigation Questions

1. Which account was targeted?
2. Which source IP generated the attempts?
3. How many failures occurred?
4. Did a successful authentication occur afterwards?
5. Was MFA enabled?
6. Is the source IP internal or external?
7. Does the activity match a known user action?

## Severity

Medium

## MITRE ATT&CK

T1110 - Brute Force

## Recommended Response

- Validate whether the activity is legitimate.
- Check for successful authentication after failures.
- Review the source IP.
- Review affected account activity.
- Reset credentials if compromise is suspected.
- Consider MFA enforcement.
- Consider rate limiting or temporary blocking.

## GRC Mapping

### NIST CSF 2.0

- DE.CM - Continuous Monitoring
- DE.AE - Adverse Event Analysis
- RS.AN - Incident Analysis

### NIST SP 800-61

- Detection and Analysis
- Containment
- Eradication and Recovery

## Evidence

Raw authentication events are stored in:

04-security-monitoring/evidence/

## Status

**Validated in laboratory environment**

The detection logic was validated through a controlled SSH authentication test and subsequently implemented and validated in Wazuh.
