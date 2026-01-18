---
title: "NixOS Standardization"
date: 2026-01-02
description: "One configuration language across the fleet. Declarative infrastructure from dev boxes to DI servers."
slug: "nixos-standardization"
showDate: true
showReadingTime: true
---

The [mental shift to config as code](/updates/config-as-code/) on the Framework was practice.

Now it was time for the real thing. NixOS across the fleet.

---

## The Problem

Every Linux machine is a snowflake. Install packages manually. Configure services by hand. Document what you did (maybe). Hope you remember it later (probably not).

Three dev boxes. Four DI servers coming. A storage server. Utility machines. Each one configured differently. Each one a liability.

And that's just Node0. Nine Ceph cluster servers waiting to be deployed. Future NodeX deployments, wherever they happen. This pattern needs to scale.

---

## The Solution

NixOS: the operating system where configuration is the system.

```nix
# This IS the machine
{ config, pkgs, ... }:
{
  networking.hostName = "dev01";

  services.openssh.enable = true;
  services.tailscale.enable = true;

  users.users.cps = {
    isNormalUser = true;
    extraGroups = [ "wheel" "docker" ];
  };

  environment.systemPackages = with pkgs; [
    git vim htop ripgrep
  ];
}
```

Rebuild: `nixos-rebuild switch`

The machine becomes what the config describes. Deterministically. Reproducibly.

---

## The Structure

One git repo. All machine configs.

```
node0-config/
├── flake.nix           # Entry point
├── hosts/
│   ├── dev01/
│   │   └── configuration.nix
│   ├── dev02/
│   ├── dev03/
│   ├── di01/
│   ├── di02/
│   ├── di03/
│   └── di04/
├── modules/
│   ├── common.nix      # Shared config
│   ├── dev-machine.nix # Dev box specifics
│   ├── di-server.nix   # DI server specifics
│   └── nvidia.nix      # GPU config
└── home/
    └── cps.nix         # Home Manager config
```

Add a new machine: create a directory, write a config, deploy.

---

## What This Enabled

**Consistency.** Every machine has the same base. Same user setup. Same SSH config. Same monitoring tools.

**Reproducibility.** Blow away a machine, rebuild from config. Same result every time.

**Visibility.** Want to know what's on a machine? Read the config. It's right there.

**Collaboration.** Claude can read and modify configs. We iterate on infrastructure together, in code.

**Disposable compute.** This is the big one. With [centralized storage on nexus](/updates/the-storage-foundation/), the machines themselves become disposable. Important data lives on ZFS, not local drives. NFS mounts connect every machine to the same datasets. If a machine dies, rebuild it from config, mount the storage, keep working. The compute is replaceable. The data is not.

---

## The Hard Parts

NixOS has a learning curve. The language is different. The mental model takes time.

Some things that tripped me up:

**Paths are immutable.** You can't just edit /etc/something. The system manages that. Good for reproducibility. Annoying when you're debugging.

**Generations matter.** Every rebuild creates a new generation. You can roll back. But you need to understand what you're rolling back to.

**Overlays and overrides.** When you need to modify a package, the syntax gets dense. Worth learning. Takes time.

---

## DI Server Specific

The DI servers needed extra work:

```nix
# nvidia.nix - shared GPU config
{ config, pkgs, ... }:
{
  hardware.nvidia = {
    modesetting.enable = true;
    open = false;
    nvidiaSettings = true;
  };

  services.xserver.videoDrivers = [ "nvidia" ];

  environment.systemPackages = with pkgs; [
    cudaPackages.cudatoolkit
    nvtop
  ];
}
```

One module. Applied to di01, di02, di03. di04 gets a lighter version (RTX 4060 Ti doesn't need the full stack).

---

## The Payoff

January 5th: dev01 deployed with NixOS. Took an afternoon.

January 7th: di03 and di04. Same config structure, different hardware. Took hours, not days.

January 11th: di01 and di02. The big machines. Same process. Same confidence.

Each deployment faster than the last. The configs accumulated knowledge. Modules got refined. Edge cases got handled once and stayed handled.

---

## Sovereignty Through Reproducibility

This is what sovereign infrastructure actually means:

- I can rebuild any machine from scratch
- The configuration is version controlled
- No hidden state, no manual steps forgotten
- The infrastructure is documented by being the infrastructure

If something breaks, I know what it should be. If I need more machines, I know how to make them.

Nine Ceph servers. Three Proxmox nodes. Future NodeX deployments in other locations. The patterns established here scale to all of it. Write once, deploy many.

---

*Part 7 of the Node0 build series. Next: [The DI Fleet](/updates/the-di-fleet/), bringing the GPU servers online.*

*The config-as-code approach built on what was learned in [Config as Code](/updates/config-as-code/) on the Framework.*
