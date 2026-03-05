# atomicBlue-Desktop &nbsp; [![bluebuild build badge](https://github.com/hovarak/atomicblue-desktop/actions/workflows/build.yml/badge.svg)](https://github.com/hovarak/atomicblue-desktop/actions/workflows/build.yml)

A personal **Wayblue-based** Atomic desktop image built with **BlueBuild**.

- **Base image:** `ghcr.io/wayblueorg/hyprland-nvidia-open`
- **Desktop:** Hyprland (Wayland)
- **GPU:** NVIDIA (Open kernel modules)

This repository contains the recipe + system configuration used to build the image and publish it to **GHCR**.

## What’s included

### System services
Enabled by default:
- `bluetooth.service`
- `tailscaled.service`

> Note: Tailscale login / tailnet membership is still configured per-machine (you’ll run `tailscale up` after install). Only the daemon autostart is baked in.

### Default Flatpaks

**System-wide (baseline):**
- `com.github.tchx84.Flatseal`
- `io.github.flattool.Warehouse`
- `org.kde.okular`
- `org.kde.kate`
- `org.libreoffice.LibreOffice`
- `com.github.jeromerobert.pdfarranger`

**User scope (personal apps):**
- `app.zen_browser.zen`
- `com.bitwarden.desktop`
- `com.discordapp.Discord`
- `com.valvesoftware.Steam`
- `md.obsidian.Obsidian`
- `net.mullvad.MullvadBrowser`
- `org.qbittorrent.qBittorrent`

## Installation (rebase)

> [!WARNING]
> OSTree native container rebasing is still considered experimental by Fedora. Use at your own risk:
> https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable

To rebase an existing Fedora Atomic-style install (Silverblue/Kinoite/Sericea/Wayblue, etc.) to this image:

1) Rebase to the **unsigned** image first (installs signing policy/keys):
```bash
rpm-ostree rebase ostree-unverified-registry:ghcr.io/hovarak/atomicblue-desktop:latest
systemctl reboot

2) Optional: View my github page to load Dotfiles.
