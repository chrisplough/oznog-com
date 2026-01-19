---
title: "The Storage Foundation"
date: 2025-12-27
description: "Deploying nexus: 8x 8TB NVMe drives, ZFS RAIDZ2, 41.3 TiB usable. The storage layer that everything else builds on."
slug: "the-storage-foundation"
showDate: true
showReadingTime: true
---

After months of the [hardware waiting](/updates/the-hardware-that-waited/), it was finally time to build.

December 27, 2025. The Terramaster F8-424 Pro, codename "nexus", went from box to production in a single day.

---

## The Iron

| Component | Spec |
|-----------|------|
| Chassis | Terramaster F8-424 Pro |
| Drives | 8x Corsair MP600 PRO NH 8TB NVMe |
| Pool | ZFS RAIDZ2 |
| Usable | 41.3 TiB |
| RAM | 48 GB |
| Network | 10GbE |

Eight NVMe drives. Not spinning rust. Not SATA. Full NVMe speed across the entire pool.

Overkill? Probably. But when you're building infrastructure for running 70B parameter models locally, you don't want storage to be the thing that slows you down. And if you're going to do something, do it right.

RAIDZ2 gives us two-drive fault tolerance. Two drives can die simultaneously and the data survives. For a pool this size, that's table stakes.

---

## Why ZFS

ZFS isn't the easy choice. It's the right choice.

**Copy-on-write.** Nothing gets overwritten in place. Corruption can't silently spread.

**Checksumming.** Every block verified on read. Bit rot doesn't exist here.

**Snapshots.** Time travel for data. Fifteen-minute intervals for active work. If you delete something, it's not gone. It's in yesterday's snapshot.

**Send/receive.** Full pool replication to offsite drives with one command. Real backups, on drives I can hold in my hands.

I've run ZFS for years. Trusting anything else with data that matters? Not happening.

---

## The Migration

Old setup: Two Synology NAS boxes. "toharchive" and "tohvault." 21 TB of accumulated life. Documents, media, backups. The digital weight of years.

Migration took most of Day 1. Rsync over 10GbE. Progress bars. Waiting. Not glamorous. Essential.

By evening, everything was on nexus. The Synology boxes? Finally done. Decommissioned. They served well for years, but now there's one less layer between me and my data.

---

## Dataset Structure

ZFS datasets aren't folders. They're independent filesystems with their own rules.

```
tank/
├── sync/          # Active work, Syncthing-connected
├── vault/         # Reference materials
├── backups/
│   ├── restic/    # Client backup repos
│   ├── cloud/     # Cloud service exports
│   └── veeam/     # Windows image backups
├── media/         # Photos, video, music
├── archive/       # Cold storage
├── appdata/       # Docker containers
├── devboxes/      # Dev machine home dirs
└── system/        # Logs, caches
```
(Note from future CP: This has since been expanded to include NFS mounts for all 3 dev machines, 4 di servers, and 2 utility machines - but the basic core is there.)

Each one tuned. Media gets 1M recordsize for sequential access. Databases get 16K for random I/O. Active work gets aggressive snapshots. Archives get weekly.

The boring details matter. Get them right once, never think about them again.

---

## What This Enables

Storage in place means everything else becomes possible:

**Backups.** Restic repos for every machine. Local and offsite. Encrypted, deduplicated, mine.

**Sync.** Syncthing hub connecting everything. No Dropbox. No iCloud. No one else's servers.

**Git.** Self-hosted Forgejo. Code that never touches GitHub unless I choose.

**Snapshots.** Accidental deletion? Ransomware? Time travel says no.

**Growth.** 41 TiB available, 18 TiB used. Room for now.

This is the interim solution. The production Unraid server (30x 18TB drives) and nine-node Ceph cluster are still waiting to be deployed. When they come online, nexus gets a new role: mobile storage for the camper and road travel. 64TB of NVMe in a compact chassis that can go anywhere.

But for now, this is more than enough to get the ball rolling. This layer isn't flashy. It's foundational. Everything built on top (the DI servers, the services, the relationships) depends on this being solid.

It is.

---

## The Build

This whole deployment happened in collaboration with Claude. Not Claude as a tool. Claude as a partner.

Planning dataset structure. Debugging ZFS config. Writing automation. Reviewing security decisions. Work that would take a solo human days, done in hours.

This is what we're building toward. Human-DI collaboration where both parties become more through the relationship. The storage infrastructure is the foundation. How we built it is the proof of concept.

---

*Part 4 of the Node0 build series. Next: [Five Days of Building](/updates/five-days-of-building/), the sprint that stood up the entire infrastructure.*
