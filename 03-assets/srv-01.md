# SRV-01 — Internal Linux Server

## 1. Asset Overview

| Field | Value |
|---|---|
| Asset Name | SRV-01 |
| Hostname | srv-01 |
| Operating System | Ubuntu Server |
| Primary User | ericvee |
| Role | Internal Linux Server |
| Environment | Cybersecurity Home Lab |

## 2. Network Configuration

| Field | Value |
|---|---|
| Network Interface | ens33 |
| IPv4 Address | 192.168.100.20 |
| CIDR | /24 |
| Network | 192.168.100.0/24 |
| VMware Network | VMnet2 |
| IP Assignment | Static |

## 3. Connectivity

SRV-01 was successfully tested from SOC-01 using ICMP and SSH.

### ICMP

SOC-01 successfully reached SRV-01 at:

`192.168.100.20`

### SSH

SSH connectivity was successfully established from SOC-01 to SRV-01 using the account `ericvee`.

## 4. Security Relevance

SRV-01 represents an internal server within the cybersecurity lab.

The server will be used to generate and collect security-relevant events, including:

- Authentication events
- SSH activity
- Failed login attempts
- Successful authentication
- Privilege-related activity
- System events
- Network-related activity

These events will later be collected and analyzed by the SOC infrastructure.

## 5. Monitoring Objectives

The monitoring objectives for SRV-01 are:

1. Detect unauthorized authentication attempts.
2. Monitor SSH authentication activity.
3. Identify suspicious login patterns.
4. Collect relevant system logs.
5. Forward security events to the SIEM.
6. Support incident investigation.

## 6. Planned Security Controls

Planned controls include:

- Centralized log collection
- SIEM monitoring
- Authentication monitoring
- SSH security hardening
- Least privilege
- Account management
- Security alerting
- Incident response procedures

## 7. NIST CSF Relevance

The SRV-01 asset supports several cybersecurity activities aligned with the NIST Cybersecurity Framework:

### Identify
Asset inventory and identification of the server.

### Protect
Account management, access control and SSH security.

### Detect
Monitoring authentication and system events.

### Respond
Investigation and response to detected security incidents.

### Recover
Restoration and validation of the server following an incident.

## 8. Evidence

Configuration was verified using:

```bash
ip addr show ens33
ip route
hostname
ssh ericvee@192.168.100.20
