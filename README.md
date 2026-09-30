# Logistics Network Design and Implementation

## Project Overview

This project focuses on the design and implementation of a computer network for a logistics-oriented organisation. The network was designed to support different organisational functions while providing appropriate network segmentation, resource access and management capabilities.

The project was developed in stages, beginning with the client requirements and network design and progressing to implementation and testing using Cisco Packet Tracer.

---

# Project Objectives

The main objectives of the project are to:

- Analyse the client's networking requirements.
- Design a suitable physical and logical network topology.
- Develop an IP addressing plan.
- Implement VLAN segmentation.
- Implement inter-VLAN routing.
- Provide a dedicated server network.
- Provide a dedicated network management VLAN.
- Implement secure remote management using SSH.
- Test and verify the implemented network.

---

# Network Design

The network is divided into several VLANs according to the functional requirements of the organisation.

| VLAN | Name | Purpose |
|---:|---|---|
| 10 | ADMIN | Administration users |
| 20 | OPERATIONS | Operations users |
| 30 | SERVER | Server resources |
| 40 | FUTURE | Future Floor |
| 99 | MANAGEMENT | Network device management |

## IP Addressing

| VLAN | Network | Default Gateway |
|---:|---|---|
| 10 | 192.168.28.0/27 | 192.168.28.1 |
| 20 | 192.168.28.32/27 | 192.168.28.33 |
| 30 | 192.168.28.64/28 | 192.168.28.65 |
| 40 | 192.168.28.96/27 | 192.168.28.97 |
| 99 | 192.168.28.128/28 | 192.168.28.129 |

---

# Network Components

The implemented network consists of:

- R1 router
- SW1-MAIN
- SW2-FUTURE
- Administration PCs
- Operations PCs
- Future Floor PCs
- Server
- AccessPoint-PT

R1 provides inter-VLAN routing using a router-on-a-stick configuration.

---

# Milestone 1 – Client Design Review

Milestone 1 focused on the planning and design of the proposed network.

### Deliverables

- Client Requirements
- Physical Topology
- Logical Topology
- IP Addressing Plan

The design established the VLAN structure, network segmentation and addressing scheme that were subsequently implemented during Milestone 2.

---

# Milestone 2 – Client Implementation Review

Milestone 2 focused on implementing and testing the proposed network in Cisco Packet Tracer.

### Implemented Features

- VLAN segmentation
- 802.1Q trunking
- Inter-VLAN routing
- Server VLAN
- Future Floor VLAN
- Management VLAN
- Secure SSH remote management

## SSH Implementation

SSH was implemented on:

- R1
- SW1-MAIN
- SW2-FUTURE

The network devices use VLAN 99 as the dedicated management network.

### Management Addresses

| Device | IP Address |
|---|---|
| R1 | 192.168.28.129 |
| SW1-MAIN | 192.168.28.131 |
| SW2-FUTURE | 192.168.28.132 |

SSH was tested from an authorised workstation to each network device.

---

# Testing

The implemented network was tested using:

- VLAN verification
- Trunk verification
- Default gateway connectivity
- Inter-VLAN connectivity
- Server connectivity
- Management VLAN connectivity
- SSH remote-access testing

The testing confirmed that the major network components and implemented SSH feature were functioning as intended.

---

# Project Files

## Milestone 1

The Milestone 1 folder contains:

- Client requirements
- Physical topology
- Logical topology
- IP addressing plan

## Milestone 2

The Milestone 2 folder contains:

- Cisco Packet Tracer implementation
- Implementation documentation
- Testing evidence
- SSH implementation evidence

---

# Technologies Used

- Cisco Packet Tracer
- IPv4
- VLANs
- IEEE 802.1Q
- Router-on-a-Stick
- SSH
- GitHub

---

# Project Status

**Milestone 1:** Completed

**Milestone 2:** Implemented and tested
