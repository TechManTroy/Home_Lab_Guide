# Phase 00: VM Provisioning (VirtualBox & Windows Host)
---
Goal: Create an Ubuntu Server VM and configure the network bridge to carry tagged traffic from the Netgear Switch.

## Task 1: The Windows Host Bridge
On Windows, VirtualBox cannot "create" a trunk port natively. Instead, you bridge the VM to your physical Ethernet adapter.

1. Open VirtualBox.

2. Create a New VM: Ubuntu 24.04 (64-bit).

3. Hardware: Minimum 2048MB RAM, 2 CPUs.

4. Network Settings:

 * Attached to: Bridged Adapter.

 * Name: Select your physical Netgear-connected Ethernet card (e.g., Intel(R) Ethernet Connection).

 * Advanced: Change Promiscuous Mode to Allow All. This is critical for the VM to     "see" tagged packets not addressed to the host's MAC.
---
