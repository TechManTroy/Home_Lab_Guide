# Phase 04: Verification & Connectivity SOP
### Goal: Ensure the "Sandboxed" status is active.



From the Ubuntu Server VM:

```ping 8.8.8.8``` -> Success (Internet works).

```ping [Home Router IP]``` (e.g., 192.168.1.1) -> Fail (100% loss).

```ping [Main PC Home IP]``` -> Fail (100% loss).

```ping [Portainer Web]``` -> Success
