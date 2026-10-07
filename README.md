# Cisco VTP — Configuration Revision Risk & Safe Integration

A focused Cisco Packet Tracer laboratory demonstrating VTP synchronization, Configuration Revision risk and controlled switch integration.

## Objectives
- Understand VTP Server and Client operation.
- Understand Configuration Revision.
- Reproduce the higher-revision integration risk.
- Observe VLAN database synchronization.
- Apply a controlled switch-integration procedure.
- Validate the final state with Cisco IOS commands.

## Scenarios
- [01 — Risky integration](docs/01-risky-integration.md)
- [02 — Safe integration](docs/02-safe-integration.md)
- [03 — Risk vs Safe](docs/03-risk-vs-safe.md)

## Topology
Four switches are used: VTP Server, two VTP Clients and an experimental/incoming switch.

Domain: `ACANEY-VTP` · VTP version: 1 · Pruning: disabled · Traps: disabled.

See [topology](topology/README.md).

## Repository structure
```
Cisco-VTP-Revision-Risk-Lab/
├── configurations/
├── docs/
├── labs/
├── tests/
│   └── screenshots/
├── topology/
└── README.md
```

The Packet Tracer files are in `labs/`. Technical procedures are in `docs/`. Commands are in `configurations/`. Evidence is in `tests/screenshots/`.

## Key lesson
The Configuration Revision is **not** the number of VLANs. It is used by VTP to determine which VLAN database is considered newer.

**Never integrate an unknown switch into an existing VTP environment before checking its VTP domain, operating mode, VLAN database and Configuration Revision.**

This lab demonstrates legacy VTP behavior in a controlled Packet Tracer environment. Modern designs should evaluate whether VTP is appropriate.
