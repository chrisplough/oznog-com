---
title: "Fiber: Real Bandwidth"
date: 2026-01-03
description: "Allwest Fiber: 2.5 Gbps down, 1.6 Gbps up. What real bandwidth enables for sovereign infrastructure."
slug: "fiber-real-bandwidth"
showDate: true
showReadingTime: true
---

The [storage foundation](/updates/the-storage-foundation/) was in place. The [network had a name](/updates/node0-is-real/). But the pipe to the outside world was still local point-to-point wireless internet. Good company. I've been grateful for them, but it's affected by weather and is limited to 150mbps.

Time to fix that.

---

## The Upgrade

Allwest Fiber. 2.5 Gbps down, 1.6 Gbps up. Symmetric-ish. Real bandwidth.

PTP wireless was fine for consumption. Streaming, browsing, the usual. But sovereign infrastructure needs to push as much as it pulls. Backups to offsite. Syncing between locations. Serving content. Hosting services.

The old wasn't going to cut it.

---

## What Changed

| Metric | Wireless | Allwest |
|--------|---------|---------|
| Down | 150 Mbps | 2.5 Gbps |
| Up | 150 Mbps | 1.6 Gbps |
| Latency | ~45ms | ~8ms |

The upload is the story. 150 Mbps to 1.6 Gbps. A >10x improvement.

Offsite backups that took hours now take minutes. Syncthing keeps up in real-time. Remote access feels local.

---

## The Internal Network

Fiber only matters if the internal network can use it.

10GbE throughout Node0. Every server, every workstation, connected at 10 gigabit. The bottleneck is never internal.

```
Internet (2.5G) → Router → 10GbE Switch → Servers
                                       → Workstations
                                       → DI Fleet
```

nexus serves files faster than the internet can deliver them. Local work never waits on network.

---

## What This Enables

**Remote DI work.** SSH into di01 from anywhere. The latency is low enough that interactive work feels responsive. Run inference remotely when needed.

**Real backups.** Restic to offsite storage at full speed. Daily backups complete before morning.

**Future hosting.** When services need to be exposed, the bandwidth is there. Self-hosted git, file sharing, whatever comes next.

**Symmetry.** Stop thinking about upload as a constraint. Push and pull are nearly equal now.

---

## The Upgrade Path

2.5 Gbps is a step, not the destination.

The fiber is upgradable to 8 Gbps symmetric. All that's waiting is deploying the dual Minisforum MS-01 OPNsense HA firewalls that are sitting in boxes. They can handle the full 8 Gbps. The current router can't.

When I find the time to configure and deploy them, Node0 gets another 3x bandwidth. True symmetric 8 Gbps up and down. The infrastructure is ready for it. The work continues in late nights and free moments.

---

## The Philosophy

Bandwidth is sovereignty.

When your upload is crippled, you're a consumer. You receive more than you send. The network topology assumes you're at the edge, not the center.

Symmetric bandwidth says: I'm a peer. I send as much as I receive. I host, I serve, I participate as an equal.

Node0 needed that. Now it has it. And more is coming.

---

*Part 8 of the Node0 build series. Next: [di03 and di04](/updates/di03-and-di04/), bringing the utility servers online.*
