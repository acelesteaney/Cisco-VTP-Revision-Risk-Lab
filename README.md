# Cisco VTP – Configuration Revision Risk & Safe Integration

##  Overview

This laboratory explores Cisco VLAN Trunking Protocol (VTP)
with a focus on the Configuration Revision mechanism and the
risks associated with integrating a switch containing a higher
VTP revision.

The laboratory is divided into two scenarios:

1. Risky VTP integration
2. Safe VTP integration

---

##  Objectives

- Understand the purpose of VTP
- Understand VTP Server and Client modes
- Understand the Configuration Revision number
- Observe VTP VLAN database synchronization
- Reproduce a higher-revision integration scenario
- Observe its impact on the VTP domain
- Apply a safe switch integration procedure
- Verify VTP synchronization

---

##  Topology

<img width="422" height="175" alt="Topologie" src="https://github.com/user-attachments/assets/982f78c8-1e62-4f0b-a9f6-5c8c6fd789ef" />


### Devices

| Device | VTP Mode |
|---|---|
| ACANEY-SW-VTP-SERVER | Server |
| ACANEY-SW-VTP-CLIENT-1 | Client |
| ACANEY-SW-VTP-CLIENT-2 | Client |
| ACANEY-SW-VTP-OTHER | Experimental switch |

### VTP parameters

- Domain: ACANEY-VTP
- VTP Version: 1
- Pruning: Disabled
- Traps: Disabled

---

#  Scenario 1 – Risky Integration

## Initial state

The existing VTP domain is running with:

- Revision: 8
- VLANs: 9

The experimental switch is prepared with:

- Revision: 9
- VLANs: 14

## Expected risk

A switch with a higher configuration revision can cause
the VTP domain to adopt its VLAN database.

## Observation

After establishing the trunk, the domain converged to:

- Revision: 9
- VLANs: 14

The clients synchronized with the new VLAN database.

<img width="389" height="180" alt="Risk-Client-1" src="https://github.com/user-attachments/assets/91c774cb-c00c-4f78-b9e9-5d994208a790" />
<img width="384" height="182" alt="Risk-Client-2" src="https://github.com/user-attachments/assets/c5ec78a6-730e-4570-a56f-ec2583364e29" />


---

#  Scenario 2 – Safe Integration

The experimental switch was isolated and its previous VLAN
database was removed.

The switch was then verified before being integrated into
the VTP domain.

## Final result

The switch synchronized with the existing domain:

- Revision: 8
- VLANs: 9

The existing VTP database remained unchanged.

<img width="391" height="181" alt="Safe-Client-1" src="https://github.com/user-attachments/assets/0694dc3b-9a54-409e-8dac-716bb3baa677" />
<img width="390" height="185" alt="Safe-Client-2" src="https://github.com/user-attachments/assets/c65e327d-89ce-45cf-bad1-0a38ba5baf47" />


---

#  Key Lessons

The Configuration Revision is not the number of VLANs.

It is a revision counter used by VTP to determine whether a
received VLAN database is newer than the locally stored one.

Before integrating a switch into an existing VTP environment,
its VTP state and VLAN database should therefore be verified.

---

#  Repository Contents

- `labs/` → Packet Tracer laboratory files
- `documentation/` → detailed laboratory documentation
- `screenshots/` → evidence of the different stages
- `configs/` → relevant commands and configurations
