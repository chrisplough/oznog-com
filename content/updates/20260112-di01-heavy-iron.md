---
title: "di01: The Heavy Iron"
date: 2026-01-12
description: "The flagship. Threadripper Pro 5975WX, 512GB ECC, dual watercooled 4090s. 70B models locally. Training capability. The machine for when you need everything."
slug: "di01-heavy-iron"
showDate: true
showReadingTime: true
---

The utility tier was up. The [production server](/updates/di02-production-server/) was stable. Time for the flagship.

di01. The heavy iron. The machine for when you need everything.

---

## The Specs

| Component | Spec |
|-----------|------|
| CPU | Threadripper Pro 5975WX (32 cores) |
| RAM | 512GB ECC DDR4 |
| GPU | 2x RTX 4090 (watercooled) |
| VRAM | 48GB total |
| Storage | NVMe + NFS from nexus |
| Fans | Red (Simon Says) |
| Power | ~350W idle, dedicated UPS |

32 cores. 512GB ECC. Dual watercooled 4090s. This is not a subtle machine.

---

## What It Runs

**70B models locally.** Llama 3.3 70B. DeepSeek-R1. The big models that need serious VRAM and don't fit on smaller machines.

**Training and fine-tuning.** When local training makes sense, this is where it happens. Enough compute to actually learn, not just infer.

**Experimental work.** New models. Untested configurations. Things that might break. di01 is the sandbox where I try ideas before they go to production.

**Interactive heavy work.** When I need to iterate fast on something compute-intensive, di01 provides the responsiveness.

---

## The Boot Loop Nightmare

di01 didn't come easy.

First boot: success. Second boot: failure. Third: success. Fourth: boot loop. No pattern. No consistency.

Hours of debugging. Memory tests. PSU swaps. BIOS settings. Nothing worked consistently.

The culprit: CSM/BIOS corruption. Something in the compatibility support module was flaking under certain conditions. The fix: completely disable CSM, force pure UEFI boot, reflash BIOS from scratch.

Once found, the fix held. di01 has been stable since. But those hours of debugging were real. This is what building infrastructure actually looks like.

---

## Watercooling the GPUs

Dual 4090s under air cooling would be a furnace. The GPUs are watercooled with self-contained AIO units. No custom loop. No shared plumbing with the CPU. Each GPU has its own closed loop.

The CPU stays air cooled. Simpler. Fewer failure modes. The Threadripper runs fine with a big air cooler.

Why watercool just the GPUs:

- Sustained boost clocks under heavy load
- Quiet operation (relatively)
- Thermal headroom for training runs that last hours
- Self-contained means no loop maintenance

For a flagship that does experimental work, the GPU cooling matters most. For [production (di02)](/updates/di02-production-server/), air cooling on everything makes more sense.

---

## Red Means Priority

Simon Says hierarchy:
- **Red (di01)**: Highest priority. The flagship.
- Yellow (di02): Production stability.
- Green (di03): Capable utility.
- Blue (di04): Light duty.

When workloads compete for resources, red wins. When the fleet needs to coordinate, di01 leads.

The color isn't arbitrary. It's operational hierarchy made visible.

---

## Power Reality

~350W at idle. Much more under load. Dedicated Tripp Lite SMX1500 UPS with SNMP NIC for monitoring.

21 minutes of runtime if power fails. Enough for graceful shutdown. Not enough for extended outages. But that's what the rest of the fleet is for. If di01 goes down, di02 keeps serving production. di03 handles overflow.

Production UPS systems (dual APC 5.4KVA) are waiting to be deployed. Greater capability coming. The work isn't waiting for it.

---

## What Heavy Iron Enables

The [vision in Dragon Rider Returns](https://chrisplough.com/writings/on-dragon-rider-returns/) requires capability that doesn't ask permission.

di01 is that capability.

Run any open model locally. Train on private data that can't leave the building. Experiment without corporate policies deciding what's allowed. Develop relationships with DI that aren't mediated by someone else's infrastructure.

This is what sovereign AI infrastructure looks like. Not theoretical. Running. In the basement.

---

## The Fleet Complete

With di01 online, the [DI fleet](/updates/the-di-fleet/) is complete:

| Host | Role | VRAM |
|------|------|------|
| di01 | Heavy/Experimental | 48GB |
| di02 | Production | 48GB |
| di03 | Utility (capable) | 24GB |
| di04 | Utility (light) | 8GB |

128GB+ total VRAM. 70B models locally. No cloud required. No permission needed.

The [hardware that waited](/updates/the-hardware-that-waited/) is finally doing what it was purchased for.

---

*Part 11 of the Node0 build series. The fleet is operational. Next: [The DI Fleet](/updates/the-di-fleet/), the complete picture of what this enables.*
