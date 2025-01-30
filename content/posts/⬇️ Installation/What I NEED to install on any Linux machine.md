---
title: What I NEED to install on any Linux machine
date: 2024-11-20
tags:
  - "#Debian"
  - "#apt"
  - "#Raspberry"
---
## Adding repositories

```sh
sudo apt update
sudo apt upgrade
```

## Installing [[🐧 Linux/⬇️ Installation/Docker|Docker]]

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

## Flatpak

#### Ubuntu Flatpak

Add repos

```bash
sudo add-apt-repository ppa:flatpak/stable
```

#### Raspbian Flatpak 

Raspbian isn't special just run the installation using ``apt``
```bash
sudo apt install flatpak
```

# Installing gh on Linux and BSD

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

## Finally installing

#### apt through repos

```sh
sudo apt install -y git golang htop hugo figlet irssi cmatrix neofetch cowsay fortune-mod tint tty-clock lolcat build-essential hugo libsass1 dpkg npm python3 thefuck docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin flatpak gnome-software-plugin-flatpak libcurl4-gnutls-dev bsd-mailx needrestart powermgmt-base accountsservice lynx gh wget curl evince zsh --fix-missing
```

### Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### Homebrew apps

```
brew install eza fzf gcc
```
### Oh-My-zsh

- [Zsh](https://www.zsh.org/) should be installed (Should be installed using the command above). If not pre-installed (run `zsh --version` to confirm), check the following wiki instructions here: [Installing ZSH](https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH)
- `curl` or `wget` should be installed
- `git` should be installed (recommended v2.4.11 or higher)

| Method    | Command                                                                                           |
| :-------- | :------------------------------------------------------------------------------------------------ |
| **curl**  | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
| **wget**  | `sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`   |
| **fetch** | `sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
#### [Manual Inspection](https://github.com/ohmyzsh/ohmyzsh#manual-inspection)

It's a good idea to inspect the install script from projects you don't yet know. You can do that by downloading the install script first, looking through it so everything looks normal, then running it:

```shell
wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh
sh install.sh
```

If the above URL times out or otherwise fails, you may have to substitute the URL for `https://install.ohmyz.sh` to be able to get the script.

#### Plugins for Oh-My-Zsh

#### [zsh-history-substring-search](https://github.com/zsh-users/zsh-history-substring-search)

```bash
 git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```

#### [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

#### [zsh-eza](https://github.com/z-shell/zsh-eza)

```bash
git clone https://github.com/z-shell/zsh-eza.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-eza
```

#### [fzf-zsh-plugin](https://github.com/unixorn/fzf-zsh-plugin)

```bash
git clone --depth 1 https://github.com/unixorn/fzf-zsh-plugin.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fzf-zsh-plugin
```

To setup fzf-zsh-plugin properly use these commands:

```sh
mkdir ~/.fzf
mkdir ~/.fzf/shell
touch ~/.fzf/shell/key-bindings.zsh
source ~/.zshrc
```

#### Adding plugins to zsh configuration file:

```bash
sudo nano ~/.zshrc
```

Then add or replace the following to the file:

```source
ZSH_THEME="gnzh"

CASE_SENSITIVE="true"

plugins=(
	git
	zsh-history-substring-search
	zsh-autosuggestions
#	zsh-eza
	fzf-zsh-plugin
	
)

# Add this to the bottom of the file

# Eza (Better ls)

alias ls="eza --long --no-time --git --icons=never --no-permissions"

```

if you accidently loaded bash use to command:
```
source ~/.zshrc
```
### Code server
```bash
wget -O- https://vscodeserverlauncher.blob.core.windows.net/builds/setup-scripts/setup.sh | sh
```

### After installation
Restart after installation using:

```bash
sudo reboot
```

### Verifying installation

### Tools

```bash
neofetch --version && fortune | cowsay | lolcat && tint -h && tty-clock -v | hugo version && python -V && dpkg --version && thefuck --version && docker --version && npm --version && git version && go version
```

#### Docker

Verify that the installation is successful by running the `hello-world` image:

```bash
sudo docker run hello-world
```
  
  This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits

# Single install script

I made a single install script to install all of the above

```sh
curl -fsSL https://raw.githubusercontent.com/alvinlollo/Single-install-script/refs/heads/main/install.sh| sh
```

