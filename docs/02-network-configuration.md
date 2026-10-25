# VoIP Network Configuration

## 1. Initial Network Design

The Ubuntu Server initially may use VMware NAT networking.

This may cause Windows host and Ubuntu virtual machine to receive addresses from different subnets, which may complicate direct SIP client connectivity.

## 2. Solution: VMware Bridged Networking

Change he virtual machine network adapter from NAT to Bridged.

This allowes the Ubuntu virtual machine to obtain an IP address from the local network.

## 3. Current Network Addressing

| Device        | Address       | Role            |
| ------------- | ------------- | --------------- |
| Windows PC    | 192.168.1.107 | MicroSIP client |
| Ubuntu Server | 192.168.1.135 | Asterisk PBX    |
| Mobile Phone  | 192.168.1.166 | Zoiper client   |

These are the addresses observed during laboratory testing. They may change if the network uses DHCP.

## 4. Check the Ubuntu IP Address

```bash
ip addr
```

Check the routing table:

```bash
ip route
```

## 5. Test Network Connectivity

From Windows PowerShell:

```powershell
ping 192.168.1.135
```

Check SSH connectivity:

```powershell
ssh <ubuntu-username>@192.168.1.135
```

Replace `<ubuntu-username>` with the actual Ubuntu account name of your server.

## 6. Verify SIP Port

Check whether Asterisk is listening on UDP port 5060:

```bash
sudo ss -lunp | grep 5060
```

The expected result should indicate a UDP socket bound to port 5060.

## 7. VMware Configuration

1. Shut down the virtual machine if required.
2. Open the virtual machine settings.
3. Select Network Adapter.
4. Select Bridged networking.
5. Start the virtual machine.
6. Check the new IP address.
7. Test connectivity from the host computer.
