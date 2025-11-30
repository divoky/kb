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

#### Kodeky

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1
sudo dnf install rpmfusion-\*-appstream-data
# kodeky
sudo dnf4 group install multimedia
sudo dnf swap 'ffmpeg-free' 'ffmpeg' --allowerasing # Switch to full FFMPEG.
sudo dnf upgrade @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin # Installs gstreamer components. Required if you use Gnome Videos and other dependent applications.
sudo dnf group install -y sound-and-video # Installs useful Sound and Video complementary packages.
```

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
