---
title: Bash
draft: false
tags:
 - linux
 - fedora
 - bash
---
## oh-my-bash
### Instalace
```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"
```
### Konfigurace
```bash
cd ~/.oh-my-bash/custom
git clone https://github.com/powerline/fonts.git fonts
cd fonts
sh install.sh
nano ~/.bashrc
```
upravit `OSH_THEME="font"` na `OSH_THEME="agnoster"`
### Odinstalace
```bash
uninstall_oh_my_bash
```
