---
title: "Node0 Is Real"
date: 2025-12-31
description: "Network rename from TempleOfHarmony to Node0. The infrastructure has an identity now."
slug: "node0-is-real"
showDate: true
showReadingTime: true
---

December 31, 2025. Last day of the year.

The [five-day sprint](/updates/five-days-of-building/) was behind us. Storage deployed. Services running. But something was off.

The network was still called TempleOfHarmony.

---

## A Name From Another Life

TempleOfHarmony made sense once. A different phase. A different purpose.

But this infrastructure wasn't a temple. It was a node. The first node of something larger.

Names matter. They shape how you think about things. Every time I saw "templeofharmony" in a hostname, it felt wrong. A past identity on present infrastructure.

---

## The Rename

New Year's Eve. Time to make it real.

```
WiFi: TempleOfHarmony → Node0
templeofharmony.local → node0.oznog.com
toharchive → nexus
tohvault → (decommissioned)
```

The WiFi rename was the big one. 70+ devices to migrate to the new network and security. Phones, tablets, laptops, smart home devices, everything. A full day of reconnecting the digital household.

The server room subnet: 10.0.2.0/24. Clean allocation scheme for growth.

---

## The Machines

After the rename, the roster:

| Host | Role | Subnet |
|------|------|--------|
| nexus | Storage (ZFS) | 10.0.2.x |
| dev01 | Development (primary) | 10.0.2.x |
| dev02 | Development | 10.0.2.x |
| dev03 | Development | 10.0.2.x |
| cps-wks | Workstation (Windows) | 10.0.1.x |

DI servers would come later. But the foundation had a name now.

---

## What Node0 Means

Node0 isn't just a clever name. It's a statement.

**Node** because it's part of a network. Not isolated. Connected to other nodes, other infrastructure, other people working on the same problems.

**Zero** because it's the origin. The first deployment. The one that proves the pattern before it spreads.

Every node after this, wherever deployed, by whoever runs it, builds on what gets learned here.

---

## The Identity Matters

Infrastructure without identity is just hardware. Giving it a name makes it a thing you maintain, develop, care about.

Node0 is:
- Sovereign (I control it)
- Connected (it talks to the world)
- Foundational (everything else builds on it)
- Real (not theoretical, running in the basement)

The [vision articulated in Dragon Rider Returns](https://chrisplough.com/writings/on-dragon-rider-returns/) needed somewhere to live. This is where it lives.

---

## What Came Next

With identity in place, the build could accelerate.

January brought the DI servers. di01 through di04. Each one joining Node0. Each one extending what the network could do.

But the name came first. You have to know what you're building before you can build more of it.

---

*Part 6 of the Node0 build series. Next: [NixOS Standardization](/updates/nixos-standardization/), bringing declarative configuration to the entire fleet.*
