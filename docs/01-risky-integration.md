# Scenario 1 — Risky VTP Integration

## Purpose
Demonstrate the historical risk of integrating a switch containing a higher VTP Configuration Revision.

## Initial state
Existing domain: revision 8, 9 VLANs.  
Experimental switch: revision 9, 14 VLANs.

The higher revision is intentional.

## Evidence

### Capture 01 — Initial topology
The topology shows the VTP server, two clients and the isolated experimental switch.

### Capture 02 — Initial VTP domain
The server is at revision 8 with 9 VLANs in the ACANEY-VTP domain.

### Capture 03 — Higher-revision switch
The experimental switch is at revision 9 with a different VLAN database containing 14 VLANs.

### Capture 04 — State comparison
The two VTP states are compared before integration to highlight the revision mismatch.

### Capture 05 — Trunk establishment
The trunk is established, allowing VTP advertisements to be exchanged.

### Capture 06 — VTP synchronization
After synchronization, the domain converges to revision 9 and 14 VLANs.

### Capture 07 — Client propagation
The clients synchronize to revision 9 and the new VLAN database.

### Capture 08 — Final risky state
The server, clients and experimental switch show the converged VTP state.

## Result
The scenario demonstrates why the VTP state of an incoming switch must be checked before integration.
