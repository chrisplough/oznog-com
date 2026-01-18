---
title: "Config as Code: The Mental Shift"
date: 2025-11-22
description: "From imperative scripts to declarative configuration. The mental model change that made NixOS possible."
slug: "config-as-code"
showDate: true
showReadingTime: true
---

Two days into the [Framework 13 setup](/updates/framework-13-sovereign-laptop/), something clicked.

I wasn't just learning new tools. I was learning a different way of thinking about configuration.

---

## The Old Way

Twenty years of muscle memory: write scripts. Bash, PowerShell, whatever. Step-by-step instructions. Do this, then this, then this.

```bash
# The imperative approach
apt update
apt install nginx
systemctl enable nginx
systemctl start nginx
echo "server { ... }" > /etc/nginx/nginx.conf
systemctl reload nginx
```

It works. Until it doesn't. Until you need to run it again on a different machine and something's different. Until you need to know *what state the system is in* rather than *what commands were run*.

---

## The New Way

Declarative configuration flips the model. Instead of "do this," you say "be this."

```nix
# The declarative approach
services.nginx = {
  enable = true;
  virtualHosts."example.com" = {
    root = "/var/www/example";
  };
};
```

The system figures out how to get there. You describe the destination, not the journey.

---

## Why It Matters for Sovereignty

Imperative scripts are knowledge locked in your head. You remember what you ran. Maybe you wrote it down. Maybe you didn't.

Declarative configs are the system itself. The configuration *is* the documentation. Want to know what's installed? Read the config. Want to reproduce it? Apply the config somewhere else.

For sovereign infrastructure, this matters. I need to be able to rebuild any machine from scratch. I need to know exactly what's running and why. I need configuration that survives me forgetting what I did six months ago.

---

## The Bridge: Stow to Nix

On the Framework, I started with GNU Stow for dotfiles. Simple symlink management. My configs live in a git repo, Stow links them into place.

```bash
cd ~/dotfiles
stow fish
stow lazyvim
stow starship
```

It's declarative-ish. The dotfiles repo describes what should exist. Stow makes it so.

But it's training wheels for the real thing: NixOS and Home Manager on the servers.

---

## What Changed

After two days of this, I stopped thinking "what commands do I run?" and started thinking "what state do I want?"

Small shift. Huge implications.

When it came time to deploy NixOS on the servers, the mental model was already there. Configuration as program. State as code. Infrastructure you can rebuild from a repo.

The Framework taught me to think this way. The servers benefited.

---

## The Pattern

Same philosophy, different layers:

| Layer | Tool | Approach |
|-------|------|----------|
| Dotfiles | Stow | Symlinks from repo |
| Packages | Home Manager | Declarative user environment |
| System | NixOS | Declarative OS configuration |
| Secrets | sops-nix | Encrypted, versioned secrets |

Each layer: describe what you want, let the tool figure out how.

---

*Part 2 of the Node0 build series. Next: [The Tools That Stuck](/updates/the-tools-that-stuck/), which modern CLI tools earned permanent spots in the workflow.*
