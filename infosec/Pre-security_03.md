# TryHackMe — Pre Security: Cloud & Virtualization

## Cloud Computing

The cloud lets us use the power of computers without worrying about
the physical hardware. Virtual machines make this possible.

---

## Benefits of Cloud Technologies

| Benefit | What it means |
|---|---|
| **Scalability** | Scale resources up or down on demand |
| **Easy management** | No physical hardware to maintain |
| **Pay-as-you-go** | Pay only for what you actually use |
| **Security** | Managed security, compliance, backups |
| **High availability** | Redundancy built in — minimal downtime |
| **Global access** | Access from anywhere in the world |

---

## Types of Cloud

### Public Cloud
Infrastructure shared across multiple organizations.
Used by **startups** — accessible, affordable, scalable.
Examples: AWS, GCP, Azure (shared infrastructure)

### Private Cloud
Dedicated infrastructure for a single organization.
Used by **banks, healthcare** — sensitive data, strict compliance.
Examples: on-premise VMware, OpenStack

### Hybrid Cloud
Combination of public and private.
Used by **growing companies** that need both scalability and data security.
Example: sensitive data stays private, public-facing apps run on public cloud

---

## Cloud Service Models

### IaaS — Infrastructure as a Service
- Provider manages: **physical hardware only**
- You manage: OS, runtime, middleware, apps, data
- Use case: maximum control, custom environments
- Examples: AWS EC2, GCP Compute Engine, Azure VMs

### PaaS — Platform as a Service
- Provider manages: **hardware + OS**
- You manage: application code, data, configuration
- Use case: focus on building and deploying your app, not infrastructure
- Examples: Heroku, Google App Engine, AWS Elastic Beanstalk

### SaaS — Software as a Service
- Provider manages: **everything** — hardware to deployment
- You manage: nothing (just use the product)
- Use case: end-user software accessed via browser
- Examples: Gmail, Zoom, Slack, Notion

---

## IaaS vs PaaS vs SaaS — Visual Comparison

```
You manage:        IaaS          PaaS          SaaS
─────────────────────────────────────────────────────
Application        ✅ You         ✅ You         ❌ Provider
Data               ✅ You         ✅ You         ❌ Provider
Runtime            ✅ You         ❌ Provider    ❌ Provider
Middleware         ✅ You         ❌ Provider    ❌ Provider
OS                 ✅ You         ❌ Provider    ❌ Provider
Virtualization     ❌ Provider    ❌ Provider    ❌ Provider
Hardware           ❌ Provider    ❌ Provider    ❌ Provider
```

---

## Major Cloud Providers

| Provider | Company |
|---|---|
| AWS | Amazon |
| Microsoft Azure | Microsoft |
| Google Cloud Platform | Google |
| Alibaba Cloud | Alibaba |
| IBM Cloud | IBM |
| Oracle Cloud | Oracle |

---

## Why This Matters for a Go Backend Developer

- Go services are deployed on **IaaS** (EC2, GCP VMs) or **PaaS** (App Engine, Cloud Run)
- **GCP** is directly relevant — Grafana Labs, GitLab, and Canonical all use GCP or multi-cloud
- Understanding IaaS vs PaaS explains **why Docker and Kubernetes exist**:
  containers bring PaaS-like simplicity to IaaS infrastructure
- The GCP Associate Cloud Engineer certification (planned for Cycle 6)
  builds directly on this foundation

---

## Takeaways

- Cloud = using compute power without owning hardware
- Public → shared, cheap, scalable
- Private → isolated, secure, expensive
- Hybrid → best of both worlds
- IaaS → you control everything above hardware
- PaaS → you control only your app and data
- SaaS → you just use the product
