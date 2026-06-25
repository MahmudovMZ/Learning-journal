# TryHackMe — Pre Security: Week 1

## Module: Computer Fundamentals

### Inside Computer Systems
- **Motherboard** — the frame connecting all components
- **CPU** — the brain; executes instructions
- **RAM** — short-term memory; fast, volatile
- **SSD/HDD** — long-term storage; persistent
- **PSU** — powers all components
- **GPU** — handles visual output

### Types of Computers
- Laptop → mobility
- Desktop → performance
- Workstation → reliability
- Server → serves users/clients
- Smartphone → iPhone, Android
- Tablet → iPad
- IoT → smart thermostat, doorbell
- Embedded → coffee machines, ATMs

---

## Module: Client-Server Basics

### Core Concept
- **Client** — always initiates requests (e.g. browser)
- **Server** — responds with a resource or an error
- Flow: client sends request → server returns response

### Protocol
Rules that define how client and server communicate:
- What commands both understand (e.g. GET)
- How requests are formatted
- What syntax is used
- What response maps to what request
- How errors are handled

### Port
Each port = a separate service running on a system.
A port is required to access any service on a host.

### DNS
Translates human-readable domain names (google.com)
into IP addresses so the client can make the actual request.
Exists because humans can't memorize IPs.

---

## HTTP Methods
| Method | Purpose |
|---|---|
| GET | Retrieve a resource |
| POST | Submit data / create |
| PUT | Replace a resource |
| PATCH | Partially update |
| DELETE | Remove a resource |
| HEAD | GET without response body |
| OPTIONS | Check allowed methods |
| CONNECT | Establish a tunnel |
| TRACE | Diagnostic loop-back |

---

## Takeaways
- Client-server model is the foundation of everything
  on the web — including the Go REST APIs I'm building
- HTTP methods map directly to REST API design:
  GET/POST/PUT/PATCH/DELETE are the same methods
  used in Go's `net/http` package
- DNS and ports are critical for understanding
  how services are discovered and accessed —
  relevant for Go microservices architecture
