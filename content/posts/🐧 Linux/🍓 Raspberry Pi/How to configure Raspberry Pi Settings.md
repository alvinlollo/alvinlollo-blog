---
title: How to configure Raspberry Pi Settings
date: 2024-11-29
tags:
  - Raspberry
  - Debian
  - "#CLI"
---

```sh
sudo raspi-config
```

This is a command that helps change most of the Raspbian settings and automates edits to [`/boot/firmware/config.txt`](https://www.raspberrypi.com/documentation/computers/config_txt.html#what-is-config-txt). Running this command give some options to ***enable / disable* Raspbian features such as:**

## Raspberry Pi Software Configuration Tool (raspi-config)

![[Raspberry Pi Software Configuration Tool (raspi-config).png]]

- System Options - Configure system settings
- Display Options - Configure display settings
- Interface Options - Configure connections to peripherals
- Performance Options - Configure Configure performance settings
- Localization Options - Configure language and regional settings
- Advanced options - Configure advanced settings
- Update - Update the raspi-config tool to the latest version
- About raspi-config - information about this configuration tool

## How to use the menu

Use the **Up** and **Down** arrow keys to move the highlighted selection between the options available.

Press the **Right** arrow key or press **Tab** to access the `<Select>` and `<Finish>` buttons. Press **Left** or press **Tab** to return to the options.

`raspi-config` automates edits to [`/boot/firmware/config.txt`](https://www.raspberrypi.com/documentation/computers/config_txt.html#what-is-config-txt) and various Linux configuration files. Some options require a reboot to take effect. If you changed any of these, `raspi-config` asks you to reboot when you exit.

