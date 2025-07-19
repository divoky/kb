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
eval "$(ssh-agent -s)"
ssh-add
```
#### Zastavení
```bash
eval "$(ssh-agent -k)"
```

## PS1
```bash
cp /usr/share/git-core/contrib/completion/git-prompt.sh ~/
nano ~/.bashrc
```
přidat:
```bash
if [ -f ~/.git-prompt.sh ]; then  
   . ~/.git-prompt.sh  
   GIT_PS1_SHOWCOLORHINTS=1  
   PS1='${PROMPT_START@P}\[\e[${PROMPT_COLOR}${PROMPT_HIGHLIGHT:+;$PROMPT_HIGHLIGHT}m\]${PROMPT_USERHOST@P}\[\e[0m\]${PROMPT_SEPARATOR@P}\[\e[${PROMPT_DIR_COLOR-${PROMPT_COLOR}}${PROMPT_HIGHLIGHT:+;$PROMPT_HIGHLIGHT}m\]${PROMPT_DIRECTO  
RY@P}\[\e[0m\]${PROMPT_END@P}$(__git_ps1 " (%s)")\$\[\e[0m\] '  
fi
```