# VTP Lab – Commands Reference

## 1. VTP verification

```cisco
show vtp status
```

Use this command to verify:
- VTP operating mode
- VTP domain
- VTP version
- number of VLANs
- Configuration Revision
- pruning/trap status

## 2. VLAN verification

```cisco
show vlan brief
```

Use this command to verify the local VLAN database and VLAN names.

## 3. Trunk verification

```cisco
show interfaces trunk
```

Use this command to verify that the expected interface is operating as an 802.1Q trunk and that VLANs are active/forwarding.

## 4. Configure VTP domain

```cisco
vtp domain ACANEY-VTP
```

The domain must match the existing VTP environment before synchronization can occur.

## 5. Configure VTP mode

Server:

```cisco
vtp mode server
```

Client:

```cisco
vtp mode client
```

## 6. Create VLANs on the VTP server

Example:

```cisco
configure terminal
vlan 10
 name ADMIN
vlan 20
 name COMPTA
vlan 30
 name RH
vlan 40
 name IT
end
```

On a VTP Server, VLAN database changes increase the Configuration Revision.

## 7. Reset an incoming switch before integration

For a controlled lab reset, keep the switch isolated and remove the old VLAN database and startup configuration:

```cisco
enable
delete vlan.dat
erase startup-config
reload
```

After reload, verify the VTP/VLAN state before connecting the switch to the production-like VTP domain.

## 8. Verify the final state

Run:

```cisco
show vtp status
show vlan brief
show interfaces trunk
```

Compare the incoming switch with the existing VTP server and clients.

## Important note

Changing only the VTP domain name is **not** a complete reset of the VLAN database or Configuration Revision. A switch coming from another VTP environment should be inspected and properly reset before integration.

## Lab principle

**Never connect an unknown switch to an existing VTP environment before checking its VTP state.**
