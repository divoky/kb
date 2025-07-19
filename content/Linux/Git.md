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

### PS1
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
### SSH key
```bash
ssh-keygen -t ed25519 -C "<email>"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

výstup `cat ~/.ssh/id_ed25519.pub` uložit na github `Settings > SSH and GPG keys > New SSH key`

### GPG key
vygenerování klíče

```bash
gpg --full-generate-key
```

vypsání klíčů

```bash
gpg --list-secret-keys --keyid-format=long
gpg: checking the trustdb  
gpg: marginals needed: 3  completes needed: 1  trust model: pgp  
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u  
[keyboxd]  
---------  
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
```

výstup příkazu (včetně `-----BEGIN PGP PUBLIC KEY BLOCK-----` a `-----END PGP PUBLIC KEY BLOCK-----`) uložit na github `Settings > SSH and GPG keys > New GPG key`

```bash
gpg --armor --export 3AA5C34371567BD2
-----BEGIN PGP PUBLIC KEY BLOCK-----

cG7W5pj...

-----END PGP PUBLIC KEY BLOCK-----
```

přidání do git-u

```bash
git config --global --unset gpg.format
gpg --list-secret-keys --keyid-format=long
git config --global user.signingkey 3AA5C34371567BD2
git config --global commit.gpgsign true
git config --global tag.gpgSign true
[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc
```