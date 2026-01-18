---
title: "Framework 13: Sovereign Laptop"
date: 2025-11-20
description: "Framework 13 with Omarchy (Arch + Hyprland). Modern tools, sovereign computing, no compromises. The mobile foundation for everything that followed."
slug: "framework-13-sovereign-laptop"
showDate: true
showReadingTime: true
---

The [hardware had waited](/updates/the-hardware-that-waited/) for months. But before deploying servers, I needed a development environment that could drive the work.

November 2025. Framework 13 with Omarchy. The laptop that would orchestrate everything.

---

## The Machine

| Component | Spec |
|-----------|------|
| CPU | AMD Ryzen AI 9 HX 370 |
| RAM | 96GB DDR5 |
| Storage | 2.8TB NVMe (btrfs) |
| OS | Omarchy (Arch + Hyprland) |

Framework because repairable, upgradeable, not locked down. Started with 64GB RAM, upgraded to 96GB when the work demanded it. That's the point. Hardware you can modify.

Omarchy because DHH's curation philosophy aligned with mine: best modern tools, opinionated defaults, no bloat.

---

## The Philosophy

Returning to Linux after years on macOS. Last serious Linux use was 2016. A lot changed.

The decision: start fresh with the best modern tools, not legacy for compatibility.

**fd** instead of find. **ripgrep** instead of grep. **bat** instead of cat. **eza** instead of ls. **zoxide** for navigation. **yazi** for file management. **LazyVim** for editing. **fish** for interactive shell.

Modern tools that make the work faster and more pleasant. Life's too short for bad interfaces.

---

## What Omarchy Provided

Turns out DHH made similar choices. About 50% of what I wanted was already there:

- **LazyVim** configured and theme-integrated
- **lazygit** for version control
- **btop** for system monitoring
- **Docker** ready to go
- **Starship** prompt
- **fd, ripgrep, eza, zoxide** all installed

The overlap validated the approach. When two people independently reach similar conclusions, there's probably something to it.

---

## The Stack

What got added:

```bash
# Shell upgrade
fish + fisher + fzf integration

# File management
yazi + ffmpegthumbnailer

# Modern CLI tools (filling gaps)
bat, sd, git-delta

# Development
direnv, stow for dotfiles

# System safety
snapper + snap-pac for btrfs snapshots

# Sync
syncthing
```

Config as code. Stow for dotfiles now, NixOS and Home Manager for servers later. Building the muscle memory for declarative infrastructure.

---

## Why It Mattered

This laptop became the control center for everything that followed.

SSH into servers. Run deployments. Debug configurations. Write documentation. All from a machine I fully control, running software I understand, on hardware I can repair.

Mobile sovereignty. Take it anywhere. No cloud dependencies for core work.

---

## Practical Sovereignty

The goal isn't purity. It's having the choice and using what actually works.

I still use my 2021 MacBook Pro with M1 Max. It's faster at transcription than the Framework. It's the best tool for video editing, music production, recording. macOS is simply better for media work. I use both Android and iPhone. I look forward to testing GrapheneOS.

The right tool for the right problem at the right time with as much sovereignty as possible.

Funny enough, the Framework got deployed faster because I spilled a Celsius drink all over the MBP. Spent a week drying it out. Nothing like losing your primary machine to motivate getting the backup operational. The MBP survived. And now I have two sovereign laptops instead of one.

Always good to have a backup.

---

## The Pattern

The same philosophy that drove the laptop choice drove everything:

- **Sovereignty**: Control over your tools
- **Modern**: Best current options, not legacy for legacy's sake
- **Repairable**: Hardware and software you can fix
- **Connected**: Interoperates with everything, dependent on nothing

Framework + Omarchy was the proof of concept. The servers followed the same pattern with NixOS.

---

*Part 1 of the Node0 build series. Next: [The Storage Foundation](/updates/the-storage-foundation/), deploying the storage layer that everything builds on.*

*This work happened in parallel with the [Standpoint research phase](https://standpointlabs.com/updates/initial-research/). Two threads of the same mission.*
