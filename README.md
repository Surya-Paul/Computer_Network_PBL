# Smart Campus Network Design

A Cisco Packet Tracer project for a segmented university campus network. The design replaces a single flat LAN with department-specific VLANs, a hierarchical extended-star topology, and router-on-a-stick inter-VLAN routing.

## Project files

- [`1.Smart Campus Network`](1.Smart%20Campus%20Network) — Cisco Packet Tracer simulation. Open this file in Cisco Packet Tracer.
- [`3.PBL-REPORT.docx`](3.PBL-REPORT.docx) — project report with the design rationale, topology, addressing plan, implementation notes, verification results, and references.

## Network design

The topology uses a central Cisco 2960 switch (S1), departmental access switching (S2), and a server access switch (S3). A Cisco 2911 router (R1) provides inter-VLAN routing through 802.1Q trunking and router subinterfaces.

The design separates Administration, Computer Science, Library, Examination, Research, Computer Lab, and Campus Server traffic into individual Layer 2 broadcast domains. Each VLAN uses a `/27` subnet, providing 30 usable host addresses. The remaining `/27` block is reserved for growth.

| VLAN | Department or service | Subnet | Gateway |
| ---: | --- | --- | --- |
| 10 | Administration | `172.27.30.0/27` | `172.27.30.1` |
| 20 | Computer Science | `172.27.30.32/27` | `172.27.30.33` |
| 30 | Library | `172.27.30.64/27` | `172.27.30.65` |
| 40 | Examination Cell | `172.27.30.96/27` | `172.27.30.97` |
| 50 | Research Centre | `172.27.30.128/27` | `172.27.30.129` |
| 60 | Computer Lab | `172.27.30.160/27` | `172.27.30.161` |
| 70 | Campus Server | `172.27.30.192/27` | `172.27.30.193` |
| — | Reserved for expansion | `172.27.30.224/27` | — |

The Campus Server is assigned `172.27.30.194/27` and provides DNS and HTTP services. The report also describes DHCP configuration for client networks.

## Main components

- **R1:** Cisco 2911 router; default gateways and inter-VLAN routing
- **S1:** Cisco 2960 central/core-distribution switch
- **S2:** Cisco 2960 departmental access switch
- **S3:** Cisco 2960 server access switch
- **End devices:** Packet Tracer PCs and a server

## Open and review

1. Install Cisco Packet Tracer.
2. Open `1.Smart Campus Network` from this repository.
3. Review the implementation, or consult `3.PBL-REPORT.docx` for the topology, configuration approach, and verification details.

The report records successful checks for VLANs, trunks, IP addressing, inter-VLAN connectivity, DHCP, DNS, HTTP, and end-to-end communication in the Packet Tracer simulation.

## Course context

This is a Computer Networks PBL assignment (course code `BTD50112`) on LANs, VLANs, and network topologies. The project demonstrates how logical segmentation and centralized switching can improve organization and scalability in a campus network.
