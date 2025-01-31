---
title: Dockur-Windows-server-2025
date: 2024-11-21
tags:
  - apt
  - CLI
  - Debian
  - Ubuntu
  - "#Docker"
---


```yaml
services:
  windows:
    image: dockurr/windows
    container_name: windows
    environment:
      VERSION: "win11"
      KVM: /dev/kvm
#      ARGUMENTS: "--device /dev/dri"
      USERNAME: "AlvinVvm"
      PASSWORD: "ampro"
    volumes:
      - /var/lib/docker/win11:/storage
      - /home/media/files:/data
    devices:
      - /dev/kvm
      - /dev/dri
    group_add:
      - "105"
#    cap_add:
#     - NET_ADMIN
    ports:
      - 8006:8006
      - 3389:3389/tcp
      - 3389:33389/udp
    stop_grace_period: 2m
    privileged: true
    restart: unless-stopped
```

```bash
sudo docker compose logs --follow
```
