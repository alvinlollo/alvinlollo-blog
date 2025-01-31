---
title: VNC on Raspberry Pi
date: 2024-12-01
tags:
  - Raspberry
  - Debian
  - apt
  - CLI
---
Upgrade Raspbian bookworm

```bash
sudo apt-get update 
sudo apt-get dist-upgrade
```

Install necessary dependnces

```bash
sudo apt-get install -y rpi-chromium-mods python-sense-emu python3-sense-emu python-sense-emu-doc realvnc-vnc-viewer
```