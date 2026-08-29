# CMPG325 Computer Networks Project
## North-West Cold Chain Logistics – Vryburg

![Network Project](https://img.shields.io/badge/CMPG325-Computer%20Networks-blue)
![Status](https://img.shields.io/badge/Status-Milestone%201-orange)
![Cisco Packet Tracer](https://img.shields.io/badge/Simulation-Cisco%20Packet%20Tracer-red)

## Project Overview

This project involves the design, implementation, configuration and testing of a computer network for **North-West Cold Chain Logistics**, a logistics organisation based in Vryburg.

The project follows a network design and implementation process in which the client's requirements are analysed before developing the physical topology, logical topology and IP addressing plan. The proposed network will subsequently be implemented and tested using Cisco Packet Tracer.

The network design also considers the client's planned expansion into an additional floor/area and the requirement for secure network-device management using **SSH**.

---

## Client Information

| Item | Details |
|---|---|
| Client | North-West Cold Chain Logistics |
| Location | Vryburg |
| Client ID | CLI-046 |
| Project ID | CMPG325-2026-046 |
| Assigned Network | `192.168.28.0/24` |
| Networking Challenge | SSH – Secure Device Management Plane |
| Simulation Software | Cisco Packet Tracer |

---

## Project Objectives

The main objectives of this project are to:

- Analyse the networking requirements of the client.
- Design an appropriate physical network topology.
- Design an appropriate logical network topology.
- Develop an IP addressing plan using the assigned `192.168.28.0/24` network.
- Provide appropriate network connectivity and services.
- Design the network to support future expansion.
- Provide network coverage for the client's additional floor/area.
- Implement secure network-device management using SSH.
- Implement the proposed network in Cisco Packet Tracer.
- Configure and test the network to verify connectivity and functionality.
- Document the design, implementation and testing process.

---

## Network Design

The proposed network is divided into functional logical segments using VLANs:

| VLAN | Name | Purpose |
|---:|---|---|
| 10 | Administration | Administration users |
| 20 | Operations | Operations users |
| 30 | Server | Network services |
| 40 | Future Floor | Future expansion |
| 99 | Management | Network-device management and SSH |

The network uses a router to provide inter-VLAN routing, while switches provide connectivity to the different network segments.

A dedicated management VLAN (VLAN 99) is included to support secure management of network devices through SSH.

---

## IP Addressing

The client's assigned network is:

`192.168.28.0/24`

The network is divided using VLSM to provide appropriately sized subnets for the different VLANs while reserving address space for future expansion.

| VLAN | Network | CIDR | Purpose |
|---:|---|---:|---|
| 10 | `192.168.28.0` | `/27` | Administration |
| 20 | `192.168.28.32` | `/27` | Operations |
| 30 | `192.168.28.64` | `/28` | Server |
| 40 | `192.168.28.80` | `/27` | Future Floor |
| 99 | `192.168.28.112` | `/28` | Management |
| — | `192.168.28.128` | `/25` | Reserved for future expansion |

---

## Physical Network

The physical topology represents the physical placement and connection of network devices within the organisation.

The current floor contains:

- 1 Router
- 1 Main Switch
- 3 Administration PCs
- 4 Operations PCs
- 1 Server

The future expansion floor contains:

- 1 Future-Floor Switch
- 2 PCs
- 1 Wireless Access Point

The future floor is connected to the main network through an uplink from the main switch.

---

## Logical Network

The logical topology represents the organisation of the network into separate logical segments.

The proposed logical design consists of:

- Administration VLAN
- Operations VLAN
- Server VLAN
- Future Floor VLAN
- Management VLAN

Inter-VLAN communication will be provided by the router. The management VLAN will be used for secure management and SSH access to network devices.

---

## Future Expansion

The network has been designed with scalability in mind. The project brief specifies that an additional floor/area may be occupied by the client and requires network coverage.

A dedicated logical network and switch have therefore been included for the future floor. Address space is also reserved within the `192.168.28.0/24` network to allow additional devices and network infrastructure to be added as the organisation grows.

---

## SSH Secure Device Management

SSH is the assigned networking challenge for this project.

During the implementation phase, SSH will be configured on the relevant network devices to allow secure remote management. Management addresses will be provided through VLAN 99.

The SSH implementation will subsequently be verified and demonstrated in Cisco Packet Tracer.

---

## Repository Structure

The repository will be updated throughout the project as each stage is completed.

```text
CMPG325-North-West-Cold-Chain-Logistics/
│
├── README.md
│
├── Milestone-1/
│   ├── Client-Requirements/
│   ├── Physical-Topology/
│   ├── Logical-Topology/
│   └── IP-Addressing-Plan/
│
├── Packet-Tracer/
│   └── Network-Implementation.pkt
│
├── Documentation/
│
└── Evidence/
