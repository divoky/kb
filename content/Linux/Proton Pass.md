---
title: Proton Pass
draft: false
tags:
---

## Instalace

```bash
url -fsLSo /tmp/proton-pass.rpm https://proton.me/download/PassDesktop/linux/x64/ProtonPass.rpm
PP_CHECKSUM=`curl 'https://proton.me/download/PassDesktop/linux/x64/version.json' | jq -r '.Releases.[0].File.[1].Sha512CheckSum'`
echo "$PP_CHECKSUM /tmp/proton-pass.rpm" | sha512sum --check -
sudo rpm --install /tmp/proton-pass.rpm
```

## Update

```bash
sudo rpm --erase proton-pass
```

dál viz [instalace](#Instalace).