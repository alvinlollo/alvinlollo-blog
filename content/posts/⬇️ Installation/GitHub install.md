---
title: Installing gh on Linux and BSD
date: 2025-01-30
tags:
  - apt
  - CLI
  - Raspberry
  - Ubuntu
  - Debian
---

Packages downloaded from [https://cli.github.com](https://cli.github.com/) or from [https://github.com/cli/cli/releases](https://github.com/cli/cli/releases) are considered official binaries. We focus on popular Linux distros and the following CPU architectures: `i386`, `amd64`, `arm64`, `armhf`.
### Debian, Ubuntu Linux, Raspberry Pi OS (apt)
Install:

```shell
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
	&& sudo mkdir -p -m 755 /etc/apt/keyrings \
        && out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
        && cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
	&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
	&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
	&& sudo apt update \
	&& sudo apt install gh -y
```

Upgrade:

```shell
sudo apt update
```
