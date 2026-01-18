---
title: "What Would Be Different"
date: 2026-01-14
description: "Looking back at 22 months from purchase to production. What I'd do differently. What I'd do the same."
slug: "what-would-be-different"
showDate: true
showReadingTime: true
---

Twenty-two months from [hardware purchase](/updates/the-hardware-that-waited/) to [operational fleet](/updates/the-di-fleet/).

Not the fastest path. Not the slowest. The path that happened.

Looking back: what would I do differently?

---

## Start with Storage

This one I got right.

[nexus](/updates/the-storage-foundation/) went up first. ZFS. Centralized datasets. NFS exports ready before any compute came online.

Every machine that followed mounted storage from day one. No local data silos. No migration headaches later. The pattern was established early.

If you're building sovereign infrastructure, start with storage. Everything else depends on it.

---

## NixOS Earlier

I spent time on manual configurations that got replaced by [NixOS](/updates/nixos-standardization/) anyway.

The first dev boxes had hand-configured services. When NixOS came in, all that work got thrown away. Not wasted exactly, but inefficient.

If I did it again: NixOS from the first machine. Learn the hard parts early. Let every subsequent deployment benefit.

---

## Document While Building

Some of the build stories exist only in my memory and scattered chat logs.

The [boot loop nightmare on di01](/updates/di01-heavy-iron/)? I remember the fix, but the debugging steps are fuzzy. The specific BIOS settings that worked? Had to rediscover them when writing this.

Better: document in real-time. Even rough notes. The details matter and they fade fast.

---

## Test Hardware Before Storing

Some of the [hardware that waited](/updates/the-hardware-that-waited/) had issues I didn't discover until deployment. Dead memory slots. DOA components. Things that could have been RMA'd months earlier if I'd tested on arrival.

The counter-argument: I wasn't ready to deploy anyway. Testing would have been wasted time during a period when the hardware needed to wait regardless.

Still. If circumstances allow, test hardware when it arrives.

---

## What I'd Do the Same

**Buy quality.** ECC memory. Server-grade boards where it matters. The premium pays off in stability and debugging time saved.

**Centralized storage first.** Already said it. Saying it again. This decision shaped everything that followed.

**NixOS for servers.** The learning curve is real. The payoff is worth it. Declarative infrastructure changes how you think about systems.

**Tier the fleet.** Production separate from experimental. Utility separate from heavy iron. Not every workload needs the flagship.

**Build in public (ish).** These posts exist because the work is worth documenting. Not for audience. For the record. For anyone building similar infrastructure later.

---

## The Honest Answer

Most of what I'd do differently is "start sooner" or "know things I couldn't have known."

The [hardware waited](/updates/the-hardware-that-waited/) because I wasn't ready. That's not inefficiency. That's reality.

The manual configs got replaced because I didn't know NixOS yet. Learning takes time.

The documentation gaps exist because I was building, not writing. Priorities.

Twenty-two months feels long. But the [inner work](https://chrisplough.com/writings/on-returning-to-technology/) that happened during those months was necessary. The infrastructure emerged when I was ready for it to emerge.

Would I do it faster if I could? Sure. Would faster have been better? Not clear.

---

## For Others Building

If you're starting similar infrastructure:

1. **Storage first.** Always.
2. **Pick your config management early.** NixOS, Ansible, whatever. Just pick and commit.
3. **Document as you go.** You'll thank yourself.
4. **Test hardware on arrival.** If you can.
5. **Separate production from experimental.** From the start.
6. **Don't wait for perfect.** The work isn't waiting for the infrastructure to be complete. The infrastructure isn't waiting for perfect conditions.

Node0 is operational. Not finished. Never finished. But operational.

That's the goal.

---

*Part 13 of the Node0 build series. Next: [The Collaboration Model](/updates/the-collaboration-model/), how human-DI partnership made this possible.*
