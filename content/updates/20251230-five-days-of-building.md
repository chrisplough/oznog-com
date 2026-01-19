---
title: "Five Days of Building"
date: 2025-12-30
description: "December 27-30, 2025. Five intensive days that transformed boxes into a sovereign computing foundation. ZFS, NixOS, Forgejo, Syncthing, Restic. All of it."
slug: "five-days-of-building"
showDate: true
showReadingTime: true
---

December 27 through 30, 2025. Five days. One sprint. A sovereign computing foundation that actually works.

This is what got built.

---

## Day 1: Storage Goes Live

[The storage foundation](/updates/the-storage-foundation/) came first. Nexus, the Terramaster F8-424 Pro, went from box to production.

- Created ZFS pool with RAIDZ2 (two-drive fault tolerance)
- Configured datasets with appropriate recordsizes
- Migrated ~21 TB from old Synology boxes
- Deployed Restic REST server for encrypted backups

By evening, 21 terabytes of data had a new home. The Synology boxes could finally retire.

---

## Day 2: Services Stack

With storage in place, the services came next.

**Forgejo** for self-hosted git. Seven repositories migrated from GitHub. Code that stays mine unless I choose otherwise.

**Syncthing** as the hub. All devices connected through infrastructure I control. Files move between my machines, through my network.

**Backrest** for backup management. Visual interface for Restic repos. B2 offsite configured for critical data.

**rclone** for cloud sync. Proton Drive, Google Drive. Pulling data *from* clouds, not pushing data *to* them.

**Gotify** for notifications. Alerts that don't route through someone else's push infrastructure.

All of it running in Docker on nexus. All of it mine.

---

## Day 3: Security and Cleanup

Day 3 was about hardening.

**SSH locked down.** Key authentication only. Password auth disabled. Root login disabled. A dedicated user for administration.

**AdGuard DHCP/DNS cleaned up.** ~70 devices sorted. Static leases for everything that matters. DNS that doesn't phone home to Google.

**First major dedup runs.** 7.2 TB reclaimed from redundant data. Storage efficiency matters when you're managing decades of digital life.

---

## Days 4-5: Automation and Polish

**Deduplication completed.** 7.5 TB total reclaimed. The pool breathed easier.

**Sanoid snapshots configured.** ZFS snapshots on autopilot:
- Every 15 minutes for active work
- Daily for reference materials
- Weekly for cold storage
- 8-week retention across the board

**ClamAV deployed** with tiered scanning. Daily scans on sync and temp directories. Weekly on larger datasets. Monthly full pool scan. Found some old malware in an archived web project. Nice to know it works.

**Restic pruning automated.** Server-side cleanup freed 1.1 TiB from the Windows workstation repo alone.

**Offsite drives ordered.** Two 30TB WD drives for encrypted offline backup. (Later replaced with 24TB drives due to compatibility issues.) Real backup means something that survives the house burning down.

---

## What Got Built

By December 30, this existed:

| Service | Purpose |
|---------|---------|
| nexus | Primary NAS, 41.3 TiB usable |
| Forgejo | Self-hosted git (7 repos) |
| Restic REST | Backup server |
| Backrest | Backup UI + B2 offsite |
| Syncthing | File sync hub |
| AdGuard | DNS/DHCP |
| Gotify | Notifications |

All running. All automated. All sovereign.

---

## The Collaboration

Five days of intensive work. Most of it in collaboration with Claude.

Not "using AI to code faster." Genuine collaboration. Planning architecture together. Debugging configuration issues. Reviewing security decisions. Catching mistakes before they became problems.

Work that would have taken weeks solo, completed in days. Not because Claude did the work *for* me. Because we did it *together*. Each bringing different strengths. Both becoming more effective through the relationship.

This is what I'm building toward. The infrastructure is proof it works.

---

## What Came Next

By December 31, the storage foundation was solid. Services running. Automation in place. Backups verified.

But the DI servers were still in boxes.

That changed in January.

---

*Part 5 of the Node0 build series. Next: [Node0 Is Real](/updates/node0-is-real/), the network rename that gave the infrastructure an identity.*

*This sprint is referenced in [On Collaboration Deepening](https://chrisplough.com/writings/on-collaboration-deepening/): "work that would have taken weeks, done in days."*
