# College Network Design (Cisco Packet Tracer)

A comprehensive, multi-floor **college network simulation** built with **Cisco Packet Tracer**, focused on scalability, segmentation, performance, and operational security.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Goals and Design Principles](#goals-and-design-principles)
- [Campus Topology Summary](#campus-topology-summary)
- [Detailed Floor-by-Floor Design](#detailed-floor-by-floor-design)
  - [Ground Floor](#ground-floor)
  - [First Floor](#first-floor)
  - [Second Floor](#second-floor)
  - [Third Floor](#third-floor)
- [Workshops and Labs Building](#workshops-and-labs-building)
- [VLAN Architecture](#vlan-architecture)
- [Routing Strategy](#routing-strategy)
- [Scalability and Future Expansion](#scalability-and-future-expansion)
- [Security and Operations](#security-and-operations)
- [Simulation File](#simulation-file)
- [How to Open and Review the Project](#how-to-open-and-review-the-project)
- [Validation Checklist (Suggested)](#validation-checklist-suggested)
- [Known Notes](#known-notes)
- [Team Members](#team-members)

---

## Project Overview

This project simulates a real-world college network where:

- The building is segmented by floor and function.
- Devices are logically isolated using VLANs.
- Inter-VLAN communication is handled through routing.
- CCTV cameras are separated into dedicated network segments to avoid congestion in academic/administrative traffic.
- Capacity planning is included by reserving unused interfaces in each VLAN for future growth.

The objective is to produce a network that is:

- **High-performance** (reduced broadcast domains and improved traffic flow)
- **Secure** (segregation of administrative, academic, surveillance, and service traffic)
- **Manageable** (clear logical structure per department/floor)
- **Scalable** (designed for expansion without full redesign)

---

## Goals and Design Principles

1. **Segmentation by role and location** through VLANs.
2. **Reduced network congestion** by isolating CCTV traffic and distributing switch domains.
3. **Interoperability** between all required departments and units.
4. **Dynamic routing** for adaptive path selection and resilience.
5. **Future-proofing** with spare interfaces and modular topology.

---

## Campus Topology Summary

The modeled environment includes:

- Main college building with **4 floors**.
- Dedicated sections for:
  - Administrative offices
  - Academic departments
  - Lecture halls
  - IT and quality units
  - Security camera infrastructure
- Workshops and labs extensions with additional endpoint density.

High-level behavior:

- End devices connect to access switches.
- VLAN trunks propagate segmentation across switching layers.
- Router/L3 functionality provides inter-VLAN forwarding.
- Dynamic routing exchanges route knowledge and adapts to path changes.

---

## Detailed Floor-by-Floor Design

### Ground Floor

- **Graduate Affairs**: 3 PCs, 1 switch
- **Faculty Entitlements**: 3 PCs, 2 printers
- **Staff Entitlements**: 4 PCs, 1 switch
- **Financial Affairs**: 5 PCs, 3 printers
- **Hallways**: 2 cameras
- **Right Staircase**: 1 camera
- **Left Staircase**: 1 camera

### First Floor

- **Hall 1 → Hall 5**: 2 cameras per hall
- **Private Program Room 1**: 1 PC, 1 camera, 1 printer
- **Private Program Room 2**: 1 PC, 1 camera, 1 printer
- **Engineering Consultation Center**: 3 PCs, 1 switch
- **IT Unit**: 5 PCs, 1 switch, 1 printer
- **Hallways**: 4 cameras
- **Right Staircase**: 1 camera
- **Left Staircase**: 1 camera

### Second Floor

- **Hall 6 → Hall 10**: 2 cameras per hall
- **Architecture Department Council**: 2 PCs, 2 switches
- **Dean's Office**: 1 PC, 1 switch
- **Vice Dean's Office**: 1 PC, 1 switch
- **Hallways**: 4 cameras
- **Right Staircase**: 1 camera
- **Left Staircase**: 1 camera

### Third Floor

- **Hall 11 → Hall 15**: 2 cameras per hall
- **Electrical, Civil, Mechanical Engineering Councils**: each has 2 PCs, 2 switches
- **Quality Assurance Center**: 2 PCs, 2 switches
- **Hallways**: 4 cameras
- **Right Staircase**: 1 camera
- **Left Staircase**: 1 camera

---

## Workshops and Labs Building

### Workshops

1. **First Floor Workshop**: 1 camera, 3 switches, 1 printer, no routers
2. **Second Floor Workshop**: 2 cameras, 3 switches, 1 printer, no routers
3. **Third Floor Workshop**: 2 cameras, 0 switches, 3 printers, no routers
4. **Fourth Floor Workshop**: 0 cameras, 0 switches, 4 printers, no routers

### Labs on the Fourth Floor

- **Lab 1 + Lab 2**: 30 camera endpoints total, 2 printers
- **Lab 3**: 22 camera endpoints, 1 printer
- **Lab 4**: 20 camera endpoints, 1 printer

### Building Lab

- 20 camera endpoints, 1 printer, no routers

> Note: Device counts above follow the supplied project specification and reflect simulation assumptions.

---

## VLAN Architecture

The network is segmented into seven logical VLANs:

| VLAN | Name | Scope | Typical Devices |
|------|------|-------|-----------------|
| 1 | Administrative Units | Student/graduate/financial/entitlements offices | PCs, printers, switches |
| 2 | Academic Departments | Engineering/architecture councils and department areas | Primarily PCs |
| 3 | Workshops | Workshops + labs related segments | PCs, switches |
| 4 | Surveillance Cameras | Hallways, staircases, external/monitoring camera zones | Cameras |
| 5 | Lecture Halls | Hall 1 to Hall 15 | Cameras (and supporting switches where needed) |
| 6 | Technical Support & IT | IT Unit, QA Center, Engineering Consultancy | PCs, printers |
| 7 | Security & Monitoring | Security room, auditorium, safe room | Cameras, switches |

### Why VLANs in this design?

- Isolate traffic by department/function.
- Reduce broadcast overhead.
- Improve troubleshooting and policy enforcement.
- Enable per-segment security controls.

---

## Routing Strategy

This project uses **OSPF** for dynamic route selection and fast adaptation.

- OSPF (link-state protocol) supports efficient path computation via SPF (Dijkstra).
- Helps routers maintain updated topology information.
- Supports scalable design patterns and rapid convergence.

---

## Scalability and Future Expansion

A core design choice is leaving **3–4 free interfaces per VLAN/segment**, enabling:

- New devices without major rewiring
- Expansion of labs/workshops
- Additional monitoring/security endpoints
- Easier migration to larger L3 designs later

---

## Security and Operations

Key operational/security benefits:

- Camera traffic isolation reduces risk and load on academic/admin networks.
- Departmental segmentation limits fault and broadcast impact.
- Structured addressing/VLAN domains improve access control opportunities.
- Dynamic routing improves resilience to path/topology changes.

---

## Simulation File

The Packet Tracer source file in this repository:

- `lastfianlfinal.pkt`

---

## How to Open and Review the Project

1. Install **Cisco Packet Tracer** (version compatible with `.pkt` file format).
2. Open `lastfianlfinal.pkt`.
3. Inspect VLAN assignments on switches.
4. Verify trunk links and router/L3 interfaces.
5. Check dynamic routing configuration (OSPF process, networks, and neighbors).
6. Run connectivity tests (ICMP/ping) across representative VLAN endpoints.
7. Validate camera network isolation behavior.

---

## Validation Checklist (Suggested)

- [ ] Each endpoint is connected to the correct floor/department switch.
- [ ] VLAN IDs map correctly to intended logical groups.
- [ ] Trunk links carry required VLANs only.
- [ ] Inter-VLAN routing works according to policy.
- [ ] Dynamic routes are learned and stable.
- [ ] Camera VLAN does not degrade administrative/academic traffic.
- [ ] Spare interfaces are available for future growth.

---
