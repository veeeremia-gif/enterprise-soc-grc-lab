# Lab Network Design

## Overview

The cybersecurity laboratory uses an isolated VMware
network to separate the lab environment from production
systems.

## Network Configuration

| Parameter | Configuration |
|---|---|
| VMware Network | VMnet2 |
| Network Type | Host-only |
| Network | 192.168.100.0/24 |
| DHCP | Disabled |

## Virtual Machines

| Hostname | IP Address | Role | Status |
|---|---|---|---|
| SOC-01 | 192.168.100.10 | SIEM / SOC | Configured |
| SRV-01 | 192.168.100.20 | Linux Server | Planned |
| ATTACK-01 | 192.168.100.30 | Security Testing | Planned |

## SOC-01

SOC-01 is the primary security monitoring and investigation
workstation.

It will later host the SIEM and security analysis tools.

### Network Interface

- Interface: ens33
- IPv4: 192.168.100.10/24
- Network: 192.168.100.0/24

## Security Objective

The isolated network is designed to allow controlled
security testing without directly exposing the laboratory
systems to the production network.

## Evidence

The following evidence will be collected:

- VMware VMnet2 configuration
- SOC-01 network adapter configuration
- `ip addr` output
- `ip route` output
