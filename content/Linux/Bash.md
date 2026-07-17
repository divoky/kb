---
title: Bash
draft: false
tags:
 - linux
 - fedora
 - bash
created: 2026-04-26 10:13:06
modified: 2026-07-17 17:41:34
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

## ble.sh

### instalace

```bash
# prerequisities
sudo dnf install git make gawk
sudo mkdir /var/src
sudo chown 1000:1000 /var/src
cd /var/src
git clone --recursive --depth 1 --shallow-submodules https://github.com/akinomyoga/ble.sh.git
make -C ble.sh install PREFIX=~/.local
echo 'source -- ~/.local/share/blesh/ble.sh' >> ~/.bashrc
```

## Historie

Do `/etc/bashrc` přidat

```bash
 export HISTSIZE=10000  
 export HISTFILESIZE=10000  
 export HISTTIMEFORMAT="%y-%m-%d %T "  
 # avoid duplicates..  
 export HISTCONTROL=ignoredups:erasedups  
 # append history entries..  
 shopt -s histappend
```

## Tipy triky

* přenos souborů
    ```bash
  cd /path/to/source/files && tar -cf - . | ssh user@127.0.0.1 'cd /path/to/destination && tar -xvf -'
    ```