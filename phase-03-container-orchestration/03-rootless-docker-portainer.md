# Phase 03: Rootless Docker & Portainer
### Goal: Deploy the container environment.

SOP: Installation Script
Run these commands as the non-root user:



### Install Rootless Docker
```
curl -fsSL https://get.docker.com/rootless | sh
export DOCKER_HOST=unix:///run/user/$(id -u)/docker.sock
```

### Start Portainer (Rootless)
```
docker run -d -p 9443:9443 --name portainer \
    --restart=always \
    -v /run/user/$(id -u)/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce:latest
```
