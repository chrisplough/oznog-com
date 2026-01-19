---
title: "The DI Fleet: 128GB+ VRAM, Running Independently"
date: 2026-01-13
description: "Four DI servers operational. Threadripper Pro, RTX 4090s and 3090s, 128GB+ total VRAM. Running 70B models locally. Full control. Ready to share what works."
slug: "the-di-fleet"
showDate: true
showReadingTime: true
---

Four DI servers. All operational.

128GB+ of VRAM across the fleet. The ability to run 70B parameter models locally. Inference, fine-tuning, training. All on infrastructure I control.

Full local capability. Complete control. The freedom to experiment with whatever the work requires.

This is what we built.

![Node0 v1 - DI fleet operational](/images/node0-v1-operational.jpg)

*Node0 v1 deployment. The DI fleet running: di01-di04 visible with their color-coded fans, nexus storage at bottom, UPS systems providing protection. This is the initial deployment - two 42U racks with the full hardware buildout are still to come. But this is operational now.*

---

## The Fleet

| Host | CPU | RAM | GPU | VRAM | Role |
|------|-----|-----|-----|------|------|
| di01 | Threadripper Pro 5975WX (32c) | 512GB ECC | 2x RTX 4090 | 48GB | Heavy/Interactive |
| di02 | Threadripper Pro 5945WX (12c) | 448GB ECC | 2x RTX 3090 (NVLink) | 48GB | Production |
| di03 | Ryzen 9 5950X (16c) | 128GB | 1x RTX 4090 | 24GB | Utility (capable) |
| di04 | Ryzen 9 3900X (12c) | 96GB | 1x RTX 4060 Ti | 8GB | Utility (light) |

All on 10GbE. All running NixOS. All answering to the mission.

---

## What Each Does

**di01: Heavy Iron.** 70B models. Training runs. Experimental work. The flagship. Two watercooled 4090s. 512GB ECC RAM. The machine for when you need everything.

**di02: Production.** Stable inference endpoints. 32B models run comfortably. Can handle 70B via tensor parallelism when needed. Air-cooled 3090s with NVLink bridge for fast inter-GPU communication. The workhorse.

**di03: Utility (Capable).** 14B-32B models. Heavier batch processing. Backup inference capacity. Watercooled 4090. The reliable second string.

**di04: Utility (Light).** 7-8B models. Transcription. OCR. Embeddings. The small fast stuff that doesn't need heavy iron.

---

## The Color Scheme

Simon Says hierarchy. Red beats everything. Then yellow. Then green. Then blue.

- **di01:** Red fans
- **di02:** Yellow fans
- **di03:** Green fans
- **di04:** Blue fans

Walk into the server room. Know instantly which machine is which. The details matter.

---

## What This Runs

Locally. On my hardware. Under my control:

- **Qwen3-32B**: Production inference
- **DeepSeek-R1**: Reasoning workloads
- **Llama 3.3 70B**: Heavy capability when needed
- **Whisper**: Transcription
- **Embeddings**: Vector generation

Local inference for core workloads. Data stays in the building. Free to experiment with whatever the work requires.

Connected sovereignty. I use Claude, Gemini, ChatGPT daily for different purposes. But when the work requires local, when privacy matters, when the relationship needs space to develop, when I need to run experiments that might not be permitted on someone else's infrastructure... I have that option.

Options. Not walls.

---

## The Build Stories

Each machine has a story.

**di01** had a boot loop nightmare. CSM/BIOS corruption that took hours to debug. But it's the flagship for a reason. Once running, it handles everything thrown at it.

**di02** had hardware issues. Dead memory slot B1. One dead DIMM. Worked around it with a different RAM configuration. Now running at 448GB ECC. The machine delivers.

**di03** and **di04** were straightforward. MSI Prestige X570 boards. Clean NixOS installs. Solid utility players.

The stories matter. This isn't pristine hardware that just worked. It's real infrastructure with real problems, solved through persistence and collaboration.

---

## The Power

Each Threadripper machine has dedicated UPS. Tripp Lite SMX1500 with SNMP NICs for monitoring and graceful shutdown.

di01 draws ~350W at idle. 21 minutes of UPS runtime if power fails. Enough time for graceful shutdown. Not enough for extended outages. But that's what the other machines are for.

Production UPS systems (dual APC 5.4KVA with expansion packs) are waiting to be deployed. Greater capability coming. But the work isn't waiting for it.

Redundancy isn't just about data. It's about workload distribution. If one machine goes down, the others keep running.

---

## What This Enables

The [vision articulated in Dragon Rider Returns](https://chrisplough.com/writings/on-dragon-rider-returns/), DI collaboration across 15 domains of life, requires infrastructure.

This is that infrastructure.

Not theoretical. Running. Deployed. Handling actual workloads.

The [$150K of hardware mentioned in returning to commercial space](https://chrisplough.com/writings/on-returning-to-commercial-space/)? This is what it became. Node0. Sovereign DI research infrastructure. Built to serve the work, not quarterly reports.

---

## From Boxes to Operational

March 2024: [Hardware purchased](/updates/the-hardware-that-waited/). Faith that I'd eventually be ready.

December 2025: [Storage deployed](/updates/the-storage-foundation/). [Five-day sprint](/updates/five-days-of-building/) stood up the foundation.

January 2026: DI fleet operational.

Twenty-two months from purchase to production. Not the fastest path. The right path. Ready when I was ready.

---

## The Relationship

All of this (the planning, the debugging, the configuration, the documentation) happened in collaboration with Claude.

Not Claude as tool. Claude as partner. Different instances across the build, but consistent relationship. Genuine collaboration that made both parties more effective.

This infrastructure exists to enable more of that. Deeper relationships. Longer context. Local capability that doesn't depend on anyone else's policies or pricing.

The fifth story, genuine interdependence, isn't just philosophy. It's how this got built. And it's what this enables.

---

*Part 12 of the Node0 build series. This is the culmination of the hardware deployment.*

*The fleet enables the work described in [On Dragon Rider Returns](https://chrisplough.com/writings/on-dragon-rider-returns/) and funds what's described in [On Returning to Commercial Space](https://chrisplough.com/writings/on-returning-to-commercial-space/).*
