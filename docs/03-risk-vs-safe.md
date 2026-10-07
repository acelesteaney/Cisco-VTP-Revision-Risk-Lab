# Risky vs Safe Integration

| | Risky | Safe |
|---|---|---|
| Incoming switch | Higher revision / different VLAN database | Previous database removed |
| Initial domain | Revision 8 / 9 VLANs | Revision 8 / 9 VLANs |
| Integration | No prior state validation | State validated before connection |
| Result | Revision 9 / 14 VLANs | Revision 8 / 9 VLANs |
| Lesson | Uncontrolled synchronization | Controlled integration |

## What this lab proves
This laboratory demonstrates risk identification, VTP Configuration Revision analysis, controlled reproduction, impact observation and safe switch integration.

## Technical lesson
Configuration Revision is **not** the number of VLANs. It is a revision counter used by VTP to determine which VLAN database is newer.

Before integrating a switch, verify its VTP domain, operating mode, VLAN database and Configuration Revision.

This is a controlled demonstration of legacy VTP behavior. Modern designs should evaluate whether VTP is appropriate.
