# ISP Connectivity Extension
## North-West Cold Chain Logistics Network

### 1. Overview

This project is an optional extension to the North-West Cold Chain Logistics network developed for the CMPG 325 Computer Networks project.

The original network focused on internal communication, VLAN segmentation, inter-VLAN routing, server services, and secure device management using SSH. This extension expands the network by introducing a simulated Internet Service Provider (ISP) connection to demonstrate how the organization could communicate with external network services.

The extension was developed to explore additional networking concepts and demonstrate initiative beyond the original implementation requirements.

**Important:** This is a post-submission extension and is separate from the original submitted technical report.

### 2. Objectives

The objectives of this extension are to:

- Extend the internal network to a simulated external network.
- Configure a WAN connection between the enterprise router and an ISP router.
- Implement routing between the internal network and the external network.
- Configure Network Address Translation with Port Address Translation (NAT/PAT).
- Test connectivity between internal client devices and an external server.
- Preserve the functionality of the existing VLANs, DHCP, DNS, and SSH configuration.

### 3. Network Topology

The extension introduces two additional devices:

- **ISP:** A Cisco 2911 router representing the Internet Service Provider.
- **EXTERNAL-SRV:** A server representing an external service, such as a cloud-hosted logistics application or a logistics partner's service.

The existing Cisco 2911 router, R1, connects the internal network to the ISP router. The ISP router connects to the external server.

#### Topology

```text
Administration PCs ─┐
Operations PCs ─────┤
Future Floor PCs ───┼── SW1-MAIN / SW2-FUTURE
Internal Server ────┘            |
                                  |
                           R1 (Cisco 2911)
                                  |
                              WAN Link
                           203.0.113.0/30
                                  |
                           ISP (Cisco 2911)
                                  |
                         External Network
                         198.51.100.0/24
                                  |
                            EXTERNAL-SRV
                           198.51.100.10
```

*Replace this text diagram with a screenshot of the actual Packet Tracer topology if available.*

### 4. IP Addressing

#### WAN connection

| Device | Interface | IP address | Subnet mask |
|---|---|---|---|
| R1 | GigabitEthernet0/1 | 203.0.113.1 | 255.255.255.252 |
| ISP | GigabitEthernet0/0 | 203.0.113.2 | 255.255.255.252 |

#### External network

| Device | Interface | IP address | Subnet mask | Default gateway |
|---|---|---|---|---|
| ISP | GigabitEthernet0/1 | 198.51.100.1 | 255.255.255.0 | N/A |
| EXTERNAL-SRV | FastEthernet0 | 198.51.100.10 | 255.255.255.0 | 198.51.100.1 |

The addresses `203.0.113.0/24` and `198.51.100.0/24` are reserved documentation ranges used here for the simulation.

### 5. Implementation

#### 5.1 WAN configuration

The WAN link connects R1 to the ISP router using the `203.0.113.0/30` subnet. Both interfaces were configured with their respective addresses and enabled.

#### 5.2 Routing

A default route was configured on R1 to forward traffic for unknown destinations to the ISP router.

```text
ip route 0.0.0.0 0.0.0.0 203.0.113.2
```

A route back to the internal network was configured on the ISP router.

```text
ip route 192.168.28.0 255.255.255.0 203.0.113.1
```

#### 5.3 NAT/PAT

NAT/PAT was configured on R1 to translate traffic from the internal network when it travels through the WAN interface.

The internal network is identified using an access control list:

```text
access-list 1 permit 192.168.28.0 0.0.0.255
```

The VLAN subinterfaces on R1 were configured as NAT inside interfaces, while `GigabitEthernet0/1` was configured as the NAT outside interface.

The translation rule uses the WAN interface address and overload:

```text
ip nat inside source list 1 interface GigabitEthernet0/1 overload
```

This allows multiple internal devices to share the WAN interface address when accessing the simulated external network.

### 6. Testing and Verification

The following tests were performed during implementation.

| Test | Purpose | Result |
|---|---|---|
| R1 to ISP router ping | Verify WAN connectivity | Successful |
| R1 to external server ping | Verify routing to the external network | Successful |
| Internal PC to external server ping | Verify external connectivity from the LAN | Successful |
| NAT/PAT verification | Inspect address translation and NAT statistics | Successful |

The reported successful tests confirm that the simulated external connection is functional for the tested devices.

Further validation should confirm connectivity from each client VLAN and verify that the existing SSH management access remains operational after the extension.

#### Evidence to include

Add screenshots of:

1. The complete Packet Tracer topology.
2. The successful WAN connectivity test.
3. A successful internal-PC-to-external-server ping.
4. The output of `show ip nat translations`.
5. The output of `show ip nat statistics`.
6. Any additional VLAN and SSH regression tests.

Store these screenshots in the `Testing-Evidence/` folder.

### 7. Relevance to Logistics

External connectivity could support a logistics organization by enabling communication with cloud-hosted applications, shipment tracking services, customers, suppliers, and external logistics partners.

The simulation demonstrates the networking foundation for such connectivity. It does not represent a connection to the real public Internet or a production-ready enterprise security design.

### 8. Conclusion

This extension expands the original North-West Cold Chain Logistics network by introducing a simulated ISP, WAN connectivity, routing, and NAT/PAT.

Successful connectivity tests demonstrated communication between the internal network and the external server. The extension provided practical experience with WAN configuration, default routing, address translation, and network testing.

The work is documented separately from the original project submission to preserve the distinction between the assessed implementation and subsequent development.

### 9. Project Files

- `ISP_Extension.pkt` — Packet Tracer file containing the extended topology.
- `Testing-Evidence/` — Screenshots demonstrating configuration and verification.
- `Design-Notes.md` — Optional additional notes on implementation decisions and troubleshooting.

