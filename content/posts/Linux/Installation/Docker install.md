---
title: Installing Docker
date: 2024-01-30
tags:
  - Debian
  - apt
  - CLI
  - Ubuntu
  - Docker
---
##  [[Docker install]] Single command install:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

## [[Flatpak installation]] 

#### Install manually

Run the following command to uninstall all conflicting packages:
```sh
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

#### Raspbian Docker

Set up Docker's `apt` repository.

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/raspbian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/raspbian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

##### After installation
Install the Docker packages.
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Verify that the installation is successful by running the `hello-world` image:

```bash
sudo docker run hello-world
```
  
  This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

#### Ubuntu Docker

Set up Docker's `apt` repository.


```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

##### After installation
To install the latest version, run:

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugn
```

Verify that the installation is successful by running the `hello-world` image:
 
```bash
sudo docker run hello-world
```
  
 This command downloads a test image and runs it in a container. When the container runs, it
 prints a confirmation message and exits.

