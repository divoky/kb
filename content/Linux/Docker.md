---
title: Docker
draft: false
tags:
 - docker
 - linux
 - fedora
 - bash
created: 2026-04-26 10:13:06
modified: 2026-05-02 17:25:15
---
## Instalace

```bash
sudo dnf -y install dnf-plugins-core
sudo dnf-3 config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
sudo docker run hello-world
```

## Cleanup

```bash
sudo docker system prune --all
sudo docker volume prune --all
```