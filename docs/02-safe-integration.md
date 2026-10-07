# Scenario 2 — Safe VTP Integration

## Purpose
Demonstrate a controlled procedure for integrating an incoming switch.

## Procedure
The switch is isolated first. Its previous VLAN database and configuration are removed before integration.

## Evidence

### Capture 09 — Incoming switch isolated
The experimental switch is isolated from the existing VTP domain.

### Capture 10 — VTP state inspection
The domain, operating mode, VLAN count and revision are inspected before connection.

### Capture 11 — VLAN database reset
The previous VLAN database is removed before integration.

### Capture 12 — Clean VTP state
The switch is verified in a clean state.

### Capture 13 — Correct VTP domain
The incoming switch is configured with the expected ACANEY-VTP domain while isolated.

### Capture 14 — Safe trunk integration
The cleaned switch is connected through the trunk.

### Capture 15 — Safe synchronization
The incoming switch adopts the existing VTP database.

### Capture 16 — Final safe state
The existing domain remains at revision 8 with 9 VLANs and the incoming switch synchronizes correctly.

## Result
The integration is controlled because the incoming switch is inspected and reset before participating in the VTP environment.
