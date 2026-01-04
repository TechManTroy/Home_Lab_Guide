# Phase 01: Network Isolation & Netplan (Ubuntu Guest)
Goal: Configure the Ubuntu guest to perform the 802.1Q tagging itself, creating an isolated sub-interface.

### Task 1: Netplan Configuration
In VirtualBox, the first interface is usually enp0s3. We will create a virtual interface enp0s3.10 for your Sandbox.


File: /etc/netplan/00-installer-config.yaml

```
YAML

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s3:
      dhcp4: no   # The main interface stays 'dark' on the home network
  vlans:
    vlan10:
      id: 10
      link: enp0s3
      addresses: [10.0.10.5/24] # Your Reserved Lab IP
      routes:
        - to: default
          via: 10.0.10.1        # Gateway of your isolated VLAN
      nameservers:
        addresses: [1.1.1.1, 8.8.8.8]
```

### Task 2: Netgear Switch Configuration (Reference)
For the packets to reach your VM, your Netgear 8-port managed switch must be configured as follows:

Port connected to Windows PC: Must be a Trunk Port (Tagged for VLAN 10).

PVID: Keep the PVID as 1 (or your standard home network ID) so your Windows Host keeps its normal internet connection.
