---
title: Git
draft: false
tags:
 - git
 - linux
 - fedora
 - bash
---
## Instalace

```bash
sudo dnf install git
```
## Konfigurace

### SSH agent
#### Spuštění
```bash
$ eval "$(ssh-agent -s)"
$ ssh-add
```
#### Zastavení
```bash
$ eval "$(ssh-agent -k)"
```