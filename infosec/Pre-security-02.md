# TryHackMe — Pre Security: Virtualization Basics

## The Problem Before Virtualization

The old rule: **"one server — one application"**

This model was:
- **Expensive** — dedicated hardware per app
- **Inefficient** — most server resources sat idle
- **Slow to deploy** — new app = new physical server
- **Hard to scale** — adding capacity meant buying hardware

---

## What Virtualization Introduced

The idea: run **multiple services/applications on a single physical server**.

This was made possible by a virtualization layer called a **Hypervisor** — a program that sits between physical hardware and virtual machines, distributing resources and allowing each VM to operate as if it were a completely separate server.

---

## Virtual Machine (VM)

Each VM is an isolated environment with:
- Its own **OS**
- Its own **software and configuration**
- Its own **allocated CPU, RAM, and storage**

Despite sharing the same physical hardware, VMs operate **independently** of each other. One VM crashing does not affect others.

---

## Hypervisor

A hypervisor is the **manager/program** responsible for creating and controlling VMs. It:
- Divides a physical machine into multiple virtual ones
- Allocates CPU, memory, and storage to each VM
- Keeps all VMs isolated from one another

---

## Two Types of Hypervisors

### Type 1 — Bare Metal
Runs **directly on hardware** — no underlying OS required.

### Type 2 — Hosted
Runs **on top of an existing OS** (Windows, macOS, Linux).

---

## Comparison

| Feature | Type 1 (Bare Metal) | Type 2 (Hosted) |
|---|---|---|
| Runs on | Physical hardware directly | Existing OS |
| Performance | High — no OS overhead | Lower — OS layer adds latency |
| Efficiency | Maximum resource utilization | Shares resources with host OS |
| Setup complexity | Complex, requires configuration | Simple, installs like any app |
| Isolation | Full hardware-level isolation | Dependent on host OS stability |
| Use case | Production servers, data centers | Testing, development, learning |
| Examples | VMware ESXi, Microsoft Hyper-V, Xen | VirtualBox, VMware Workstation, Parallels |
| Who uses it | Enterprise, cloud providers | Developers, beginners, QA engineers |

---

## Why This Matters for a Go Backend Developer

- Production Go services run inside VMs or containers on **Type 1 hypervisors** in cloud environments (AWS, GCP, Azure)
- Local development and testing often uses **Type 2** (VirtualBox, Parallels)
- Understanding virtualization explains why Docker containers exist — they solve the overhead problem that VMs introduced
- Kubernetes orchestrates containers the same way hypervisors orchestrate VMs — same concept, different abstraction layer

---

## Takeaways

- Virtualization solved the "one server one app" inefficiency
- Hypervisor = the manager between hardware and VMs
- Type 1 = fast, production-grade, runs on bare metal
- Type 2 = easy, learning-grade, runs on your laptop
- VMs → Containers → Kubernetes: each layer is an evolution of the same core idea
