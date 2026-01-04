# Phase 02: SSH Hardening & "Easy SSH"
Goal: Secure the box and simplify access from your Main PC and Laptop.

### Task 1: Disable Passwords
---
Edit ```/etc/ssh/sshd_config``` on the Ubuntu Server:


```
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM no
```
Apply: `` sudo systemctl restart ssh```

### Task 2: Client Configuration
---
On your Windows Main PC and Laptop, create/edit ``` ~/.ssh/config (usually C:\Users\YourName\.ssh\config):```

```
Plaintext
```
```
Host lab-server
    HostName 10.0.10.5
    User ubuntu
    IdentityFile ~/.ssh/id_ed25519
    Port 22
```
Now you can simply type ssh lab-server to connect.
