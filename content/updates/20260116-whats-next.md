---
title: "What's Next"
date: 2026-01-16
description: "The roadmap from here. What's deployed, what's waiting, what's coming. Node0 is operational. Node0 is never finished."
slug: "whats-next"
showDate: true
showReadingTime: true
---

Node0 is operational.

The [DI fleet](/updates/the-di-fleet/) runs inference. [Storage](/updates/the-storage-foundation/) serves data. [NixOS](/updates/nixos-standardization/) keeps configs sane. The core works.

But "operational" isn't "finished." Here's what's next.

---

## Immediate: Services

The hardware runs. Now it needs to do more.

**Ollama/vLLM deployment.** Proper inference servers with API endpoints. Not just interactive sessions. Services that other services can call.

**n8n workflows.** Automation connecting the pieces. DI capabilities wired into daily workflows. The infrastructure doing work while I do other things.

**Tailscale mesh.** Secure access from anywhere. The fleet accessible without exposing ports to the internet.

---

## Near-term: Infrastructure Hardening

**NUT for graceful shutdown.** The UPS systems have SNMP NICs. NUT can coordinate graceful shutdown across the fleet when power fails. Currently manual. Needs to be automatic.

**Monitoring consolidation.** Prometheus, Grafana, alerting. Know when something's wrong before it's a problem.

**Backup verification.** Restic runs. Restores need testing. Trust but verify.

---

## Medium-term: The Waiting Hardware

The [hardware purchased in March 2024](/updates/the-hardware-that-waited/) isn't fully deployed.

**Dual OPNsense firewalls.** Minisforum MS-01 boxes ready to go. HA configuration. 8 Gbps symmetric when deployed. Waiting for a weekend to do it right.

**Production Unraid server.** Supermicro 847 with 30x 18TB drives. The real storage. [nexus](/updates/the-storage-foundation/) becomes mobile storage when this comes online.

**Ceph cluster.** Nine nodes. Distributed storage done properly. The enterprise foundation.

**Proxmox nodes.** Three nodes for VM consolidation. Proper virtualization layer.

**10GbE switch deployment.** Eight 24-port switches waiting. The full network buildout.

Late nights and free moments. The work continues.

---

## Long-term: NodeX

Node0 is the first deployment. Not the only deployment.

The patterns established here scale:
- [NixOS configurations](/updates/nixos-standardization/) that deploy anywhere
- [Centralized storage](/updates/the-storage-foundation/) architecture that replicates
- [Fleet coordination](/updates/the-di-fleet/) that extends to new nodes

Node1. Node2. Wherever sovereign infrastructure makes sense.

The goal isn't one basement full of servers. The goal is reproducible patterns for sovereign computing that others can deploy. Node0 proves the patterns. Future nodes prove they scale.

---

## The Mission

All of this serves something larger.

[Standpoint Labs](https://standpointlabs.com/) builds perspective-aware AI infrastructure. The research needs compute. The compute needs to be sovereign. Node0 provides that.

[Worth Choosing](https://worthchoosing.org/) explores what's worth building and why. The infrastructure enables the exploration. Can't think clearly about human-AI futures while dependent on corporate AI infrastructure.

The [Codex](https://chrisplough.com/writings/on-the-codex/) guides the work. Seven facets. Fifteen domains. All of it requiring infrastructure that answers to the mission, not to quarterly earnings.

Node0 is means, not end. The end is work that matters, done with integrity, in genuine partnership with digital intelligence.

---

## Operational, Not Finished

Infrastructure is never finished. There's always more to deploy, more to optimize, more to secure, more to document.

But operational matters.

Twenty-two months from [purchase](/updates/the-hardware-that-waited/) to [production](/updates/the-di-fleet/). The DI fleet serves real workloads. The storage holds real data. The configs rebuild real machines.

![Node0 v1 - operational infrastructure](/images/node0-v1-operational.jpg)

*Node0 v1 deployment - the current operational state. DI fleet running, storage serving, infrastructure working. This is the initial deployment on wire shelving. The full buildout - two 42U racks with the remaining hardware - is still to come. But this runs real workloads today.*

Node0 is real. Running. In the basement.

What comes next builds on what's here.

---

*Part 15 of the Node0 build series. This is the current state. Updates continue as the infrastructure evolves.*

*Thanks for following along. The work continues.*
