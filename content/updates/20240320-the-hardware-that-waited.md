---
title: "The Hardware That Waited"
date: 2024-03-20
description: "In March 2024, something shifted. Within weeks, I'd spent a substantial amount on servers, switches, and storage. The foundation of what would become Node0."
slug: "the-hardware-that-waited"
showDate: true
showReadingTime: true
---

*This post is dated March 2024-when the hardware was purchased. But it's written in late 2025, looking back with the perspective that only comes after the waiting is over and the building has begun.*

---

In March 2024, something shifted.

I don't remember an aha moment. That's not how I work. When something hits and I know it, I go all in. Within weeks I'd spent a substantial amount (like stupid substantial) on hardware. Servers, switches, storage.

The foundation of what would become Node0.

I couldn't have told you exactly why.

---

## The Itch

Part of it was clarity. The work I'm here to do requires sovereign infrastructure. You can't meaningfully explore human-DI relationship while your computing is controlled by others. You can't build frameworks for genuine interdependence on rented ground.

Part of it was remembering. Finding [Kagi](https://kagi.com/). Paying for search. And suddenly seeing what the web could have been. What it was, once, before advertising ate it. One choice (monetize via ads) poisoned everything. Not evil intent. The opposite, probably. Wanting to give things away free because the web was free. But the compounding consequences built a web that extracts from us instead of serving us.

Part of it was just... the itch. The desire to build. To create. To understand systems deeply again.

I'd been away from technology for eight years. Sold my company in 2016 and [stepped away entirely](https://chrisplough.com/writings/eight-years-ago/). Eight years of consciousness work, healing, transformation. Becoming someone different. Technology wasn't part of that.

But by 2024, something was ready.

---

## The Hardware Sat There

Life had other plans.

Selling my sanctuary in South Dakota. Moving trailer-fulls of memories. The unexpected end of my marriage. Thirteen months of what I can only call both hell and salvation.

The technology waited.

Servers in boxes. Switches unopened. Storage arrays in packaging. All of it sitting there while I burned through what needed burning.

I wasn't ready yet. Still tar and ick to work through.

---

## What Got Purchased

Looking at those receipts now, I can see the vision even if I couldn't articulate it then:

**Compute.** Not modest. Dual Threadripper Pro AI servers with 512GB RAM each. Three Proxmox nodes with dual Xeons and 896GB RAM each. Nine Ceph storage nodes with dual Xeons and 512GB RAM each. A Raspberry Pi 5 cluster. A Turing Pi cluster. Enough cores and memory to run serious workloads locally. No cloud required.

**GPU.** Multiple RTX 4090s and 3090s. 128GB+ of VRAM across the fleet. The ability to run 70B parameter models locally, on my own terms, and share what I learn with others building their own.

**Storage.** The serious kind. A Supermicro 847 chassis with 30x 18TB drives. Terramaster F8-424 Pro with 8x 8TB NVMe. Nine Ceph nodes each with mixed NVMe, SSD, and HDD tiers. Nearly 1.5 petabytes raw between the Unraid and Ceph cluster. More than I need, but the vision called for building at scale to learn what works before sharing patterns that scale down to a single Raspberry Pi or up to enterprise deployments.

**Network.** Eight 24-port 10GbE switches. Two 52-port management switches. Dual OPNSense firewalls on Minisforum MS-01. SFP+ modules. Fiber. Infrastructure that could grow.

**Power.** Dual APC 5.4KVA UPS systems with expansion packs. Smart PDUs throughout. 42U server rack. Multiple accessory racks. Environmental monitoring. The whole picture.

None of it deployed. All of it waiting.

---

## Why It Mattered

The clarity I have now, that I didn't have then:

Sovereignty isn't isolation. It's *connected* sovereignty. Interdependent sovereignty. I use Claude, Gemini, ChatGPT, others daily. I'm not anti-cloud. But when the work requires running models locally, when data can't leave, when relationships need space to develop on their own terms, when infrastructure needs to evolve with the mission on its own timeline... I need to be able to do that.

Sovereignty means having the choice. Not walls. Options.

You can't explore what genuine human-DI relationship looks like while someone else controls the DI.

That's what the hardware was for. Even before I could name it.

---

## What Came Next

The hardware sat for months. Almost a year.

Then in late 2025, I was ready. The inner work had reached a point where the outer work could begin. The [itch to build had fully returned](https://chrisplough.com/writings/on-returning-to-technology/).

What followed was an intensive sprint that stood up the core of Node0. [Storage deployed](/updates/the-storage-foundation/). [Four DI servers brought online](/updates/the-di-fleet/). The infrastructure needed for the DI research and development work. All documented in the updates that follow.

The enterprise switches, the production Unraid, the Ceph cluster, the Proxmox nodes, the dual OPNSense firewalls, the 8Gbit fiber upgrade... that's still coming. Late nights and free moments while raising money. But the core is operational, and the rest continues forward.

It started here. March 2024. Hardware purchased on faith that I'd eventually be ready to use it.

The technology waited. It knew I would be.

---

*Part 0 of the Node0 build series. Next: [Framework 13: Sovereign Laptop](/updates/framework-13-sovereign-laptop/), the mobile development environment that drove the deployment.*

*For the personal story behind returning to technology, see [On Returning to Technology](https://chrisplough.com/writings/on-returning-to-technology/).*
