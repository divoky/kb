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
    - Proton Pass
  sceneTemplate: templates/article.md
  ignoredFiles: []
tags:
  - linux
  - fedora
  - KDE
  - Plasma
created: 2026-05-02 17:29:33
modified: 2026-05-02 17:30:55
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
sudo dnf install ffmpeg-libs libva libva-utils
# AMD
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
# pouze pro režim kompatibility s i686 (steam, ...)
sudo dnf swap mesa-va-drivers.i686 mesa-va-drivers-freeworld.i686
sudo dnf swap mesa-vdpau-drivers.i686 mesa-vdpau-drivers-freeworld.i686
```

další info pro konkrétní HW [^2]

#### Post Install tipy

https://github.com/devangshekhawat/ [^3]

#### Tesseract language pack

```bash
sudo dnf install tesseract-langpack-ces
```

credit [^4]

### Servis

#### Nastavení počtu záloh při updatu / upgradu

Do `main` sekce v `/etc/dnf/dnf.conf` přidat `installonly_limit=13`

potom `sudo dnf upgrade --refresh`

#### Odstranení konkrétního kernelu

aktuální kernel: `uname -a`
vypsání dostupných verzí: `rpm -qa kernel`
odstranění verze včetně všech závislostí: `sudo dnf remove kernel*6.16.3*`
potom `sudo dnf upgrade`
restart (optional)

#### Firmware update

```bash
fwupdmgr refresh --force
fwupdmgr get-updates
fwupdmgr update
```

[^1]: https://discussion.fedoraproject.org/t/why-isnt-numlock-at-plasma-startup-turned-on-by-default/96799/9

[^2]: https://rpmfusion.org/Howto/Multimedia

[^3]: https://github.com/devangshekhawat/Fedora-43-Post-Install-Guide

[^4]: https://discussion.fedoraproject.org/t/install-all-languages-of-tesseract/112299/3
