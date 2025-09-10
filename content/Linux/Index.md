---
longform:
  format: scenes
  title: Linux
  workflow: Default Workflow
  sceneFolder: /
  scenes:
    - Bash
    - Docker
    - Git
  sceneTemplate: templates/article.md
  ignoredFiles: []
tags:
  - linux
  - fedora
  - KDE
  - Plasma
---
## Fedora
### Nastavení
#### Num lock
Nastavení num lock po zapnutí [^1]

`System Settings > Keyboard > Keyboard > Keyboard > Numlock on startup: Turn on`

potom

`System Settings > Apperance & Style > Colors & Themes > Global Theme > Login Screen (SDDM) > Apply Plasma Settings...`

### Servis
#### Nastavení počtu záloh při updatu / upgradu

Do `main` sekce v `/etc/dnf/dnf.conf` přidat `installonly_limit=13`

potom `sudo dnf upgrade --refresh`
#### Odstranení konkrétního kernelu

aktuální kernel

`uname -a`

vypsání dostupných verzí

`rpm -qa kernel`

odstranění verze včetně všech závislostí

`sudo dnf remove kernel*6.16.3*`

potom `sudo dnf upgrade`

restart (optional)

[^1]: https://discussion.fedoraproject.org/t/why-isnt-numlock-at-plasma-startup-turned-on-by-default/96799/9
