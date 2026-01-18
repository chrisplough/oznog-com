---
title: "di02: Production Server"
date: 2026-01-11
description: "The production inference workhorse. Threadripper Pro, 448GB ECC, dual 3090s with NVLink. Stable endpoints for real work."
slug: "di02-production-server"
showDate: true
showReadingTime: true
---

[di03 and di04](/updates/di03-and-di04/) proved the patterns. Now it was time for the production tier.

di02. The workhorse. Stable inference endpoints that don't go down for experiments.

---

## The Specs

| Component | Spec |
|-----------|------|
| CPU | Threadripper Pro 5945WX (12 cores) |
| RAM | 448GB ECC DDR4 |
| GPU | 2x RTX 3090 (NVLink bridge) |
| VRAM | 48GB total |
| Storage | mdadm RAID 1 (OS) + NFS from nexus |
| Fans | Yellow (Simon Says) |

Threadripper Pro for ECC memory. 448GB of it. When production inference serves real workloads, memory errors aren't acceptable.

Dual 3090s with NVLink bridge. 48GB of VRAM that can act as a unified pool for tensor parallelism. 32B models run comfortably. 70B models work via tensor split when needed.

---

## Why Production Separate

di01 is for experiments. Training runs. Trying new things. Breaking stuff to learn.

di02 is for stability. API endpoints that stay up. Inference that returns consistent results. The machine other systems depend on.

Separating these roles means experiments don't take down production. I can break di01 completely and di02 keeps serving.

---

## The Hardware Story

di02 wasn't clean.

Dead memory slot B1. Discovered during initial testing. One DIMM dead on arrival. Could have sent the board back. Could have waited weeks.

Instead: worked around it. Different RAM configuration. Filled the slots that work. 448GB ECC instead of theoretical maximum. Good enough. The machine runs.

This is real infrastructure. Not pristine gear that just works. Hardware with issues, solved through persistence. The work continues.

---

## Air Cooling the 3090s

Two 3090s generate serious heat. The easy answer is watercooling. The practical answer for a production server: don't add failure modes.

Air cooled with 45mm spacing between cards. Aggressive fan curves. Thermal headroom verified under sustained load.

It's louder than watercooled. It's also simpler. No pumps to fail. No loops to leak. Production servers optimize for reliability, not aesthetics.

---

## NVLink

The 3090s are NVLink bridged. Fast inter-GPU communication for tensor parallelism.

When a model needs more than 24GB VRAM, it splits across both cards. NVLink makes that split fast enough to be practical. 70B inference works. Not as fast as on di01's 4090s, but it works.

Production capability for when di01 is busy or down.

---

## The Role

di02 runs:

- **Qwen3-32B** for production inference
- **Stable API endpoints** that other services call
- **Backup 70B capability** when needed
- **Batch processing** for non-interactive workloads

Yellow fans. Second in the Simon Says hierarchy. The machine you rely on when reliability matters more than raw speed.

---

## What Production Means

Production isn't about being the fastest. It's about being predictable.

di02 serves the same inference endpoints every day. Response times are consistent. The machine doesn't go down for experiments. When I need reliable AI capability, di02 provides it.

The [DI fleet](/updates/the-di-fleet/) has tiers for a reason. di02 is the tier you depend on.

---

*Part 10 of the Node0 build series. Next: [di01: The Heavy Iron](/updates/di01-heavy-iron/), the flagship of the fleet.*
