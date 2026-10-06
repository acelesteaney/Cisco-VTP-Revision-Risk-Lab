# Cisco VTP – Configuration Revision Risk & Safe Integration

## Overview

This laboratory explores Cisco VLAN Trunking Protocol (VTP) with a focus on the Configuration Revision mechanism and the risks associated with integrating a switch containing a higher VTP revision.

The laboratory is divided into two scenarios:

1. Risky VTP integration
2. Safe VTP integration

---

## Objectives

- Understand the purpose of VTP
- Understand VTP Server and Client modes
- Understand the Configuration Revision number
- Observe VTP VLAN database synchronization
- Reproduce a higher-revision integration scenario
- Observe its impact on the VTP domain
- Apply a safe switch integration procedure
- Verify VTP synchronization

---

## Topology

The laboratory uses four switches:

| Device | Role |
|---|---|
| ACANEY-SW-VTP-SERVER | VTP Server |
| ACANEY-SW-VTP-CLIENT-1 | VTP Client |
| ACANEY-SW-VTP-CLIENT-2 | VTP Client |
| ACANEY-SW-VTP-OTHER | Experimental switch |

### VTP parameters

- Domain: ACANEY-VTP
- VTP Version: 1
- Pruning: Disabled
- Traps: Disabled

---

# Scenario 1 – Risky Integration

## Initial state

The existing VTP domain is running with:

- Revision: 8
- VLANs: 9

The experimental switch is prepared offline with:

- Revision: 9
- VLANs: 14

### Capture 01 — Initial topology

**Indicative sentence:**  
*The topology shows the VTP server, the two VTP clients and the isolated experimental switch before the risky integration.*

### Capture 02 — Initial VTP domain

**Indicative sentence:**  
*The VTP server is initially at configuration revision 8 with 9 VLANs in the ACANEY-VTP domain.*

### Capture 03 — Higher-revision switch

**Indicative sentence:**  
*The experimental switch is intentionally prepared with configuration revision 9 and a different VLAN database containing 14 VLANs.*

### Capture 04 — State comparison before integration

**Indicative sentence:**  
*Before the trunk is established, the two VTP databases are compared to highlight the revision mismatch.*

## Risky integration

The experimental switch is connected to the existing VTP domain through the trunk.

### Capture 05 — Trunk establishment

**Indicative sentence:**  
*The trunk between the existing VTP domain and the experimental switch is established, allowing VTP advertisements to be exchanged.*

### Capture 06 — VTP synchronization after integration

**Indicative sentence:**  
*After synchronization, the existing VTP domain has converged to revision 9 and 14 VLANs, demonstrating the historical risk of introducing a switch with a higher revision.*

### Capture 07 — Client propagation

**Indicative sentence:**  
*The VTP clients have also synchronized to revision 9 and the new VLAN database, showing that the change propagates through the VTP domain.*

### Capture 08 — Final risky-state verification

**Indicative sentence:**  
*The final verification confirms that the server, clients and experimental switch have converged to the same VTP revision and VLAN database.*

---

# Scenario 2 – Safe Integration

The experimental switch is first isolated from the existing VTP domain.

Its previous VLAN database and configuration are removed before integration.

### Capture 09 — Incoming switch isolated

**Indicative sentence:**  
*The experimental switch is isolated from the existing VTP domain before any integration attempt is made.*

### Capture 10 — VTP state inspection

**Indicative sentence:**  
*The VTP status of the incoming switch is inspected before connection in order to identify its domain, operating mode, VLAN count and configuration revision.*

### Capture 11 — VLAN database reset

**Indicative sentence:**  
*The previous VLAN database is removed from the incoming switch so that it cannot introduce an old or higher configuration revision into the existing domain.*

### Capture 12 — Clean VTP state

**Indicative sentence:**  
*The switch is verified in a clean state before being connected to the existing VTP environment.*

### Capture 13 — Correct VTP domain configuration

**Indicative sentence:**  
*The incoming switch is configured with the expected ACANEY-VTP domain while it is still isolated.*

### Capture 14 — Safe trunk integration

**Indicative sentence:**  
*The cleaned switch is connected to the existing VTP domain through the trunk after its VTP state has been verified.*

### Capture 15 — Safe synchronization

**Indicative sentence:**  
*After synchronization, the incoming switch adopts the existing VTP database instead of imposing its previous VLAN database on the domain.*

### Capture 16 — Final safe-state verification

**Indicative sentence:**  
*The final verification confirms that the existing VTP domain remains at revision 8 with 9 VLANs and that the incoming switch has synchronized correctly.*

---

# Risky vs Safe Integration

| | Risky integration | Safe integration |
|---|---|---|
| Incoming switch | Higher revision (9) and different VLAN database | Previous VLAN database removed before integration |
| Initial domain | Revision 8 / 9 VLANs | Revision 8 / 9 VLANs |
| Result | Domain converges to revision 9 / 14 VLANs | Domain remains at revision 8 / 9 VLANs |
| Main issue | Uncontrolled VTP database synchronization | Controlled switch integration |
| Control point | Trunk connected before validating VTP state | VTP state validated and reset before connection |

---

# What This Lab Proves

This project is not only a Packet Tracer configuration exercise.

It demonstrates the ability to:

- identify a network configuration risk;
- understand how VTP Configuration Revision influences VLAN database synchronization;
- reproduce the risk in a controlled environment;
- analyze the resulting change across the VTP domain;
- apply a controlled switch-integration procedure;
- verify the final state using operational commands.

The main lesson is that a switch should not be connected to an existing VTP environment without first checking its VTP domain, operating mode, VLAN database and Configuration Revision.

---

# Key Lessons

The Configuration Revision is **not** the number of VLANs.

It is a revision counter used by VTP to determine whether a received VLAN database is newer than the locally stored one.

Before integrating a switch into an existing VTP environment, its VTP state and VLAN database should therefore be verified.

The laboratory demonstrates a historical VTP risk in a controlled Packet Tracer environment. In modern network designs, VTP should be evaluated carefully and is often avoided in favor of explicit VLAN management or safer VTP configurations.

---

# Repository Contents

- `labs/LAB-VTP-AVEC-RISQUE.pkt` → risky integration scenario
- `labs/LAB-VTP-SANS-RISQUE.pkt` → safe integration scenario
- `screenshots/` → screenshots to be added manually
- `configs/commands.md` → key commands used in the laboratory
- `documentation/` → detailed documentation to be added later if required
