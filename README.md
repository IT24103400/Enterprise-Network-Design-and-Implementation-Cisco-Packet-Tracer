# Enterprise-Network-Design-and-Implementation-Cisco-Packet-Tracer


**Cisco Packet Tracer | Enterprise Networking | IPv4 & IPv6**

A Cisco Packet Tracer project modeling a multi-site enterprise network with a headquarters, departmental LANs, a server farm, and a branch office. The design explores scalable IP addressing, VLAN segmentation, dynamic routing, centralized address assignment, external connectivity, and network security.

> **Project status:** VLANs, DHCP, and branch routing have been configured and tested during development. NAT/PAT, IPv6, wireless access, and some security features are included in the project scope; verify their final state in the `.pkt` file and supporting screenshots before treating them as completed.

## Technologies and Concepts

- Cisco Packet Tracer and Cisco IOS CLI
- IPv4 addressing and VLSM subnetting
- VLANs, IEEE 802.1Q trunks, and inter-VLAN routing
- Multi-area OSPF routing
- Centralized DHCP and DHCP relay (`ip helper-address`)
- NAT/PAT (overload) for simulated external connectivity
- IPv6 and dual-stack networking
- Layer 2 security: port security, DHCP snooping, and BPDU Guard
- Wireless access points and DHCP clients
- Connectivity verification and troubleshooting

## Network Architecture

The simulated enterprise network includes:

- **Headquarters:** Departmental VLANs for Engineering, HR, and Sales
- **Server farm:** Centralized network services, including DHCP
- **Branch office:** A remote LAN connected to the enterprise routing infrastructure
- **Edge / ISP segment:** A simulated external network for testing routed connectivity and NAT/PAT

Add your final topology screenshot at `screenshots/network-topology.png` to display it here:

![Enterprise network topology](screenshots/network-topology.png)

## IPv4 Addressing Plan

The project uses the private address block **`192.168.1.0/24`**, divided using VLSM.

| Network | Subnet | Prefix | Example purpose |
|---|---|---|---|
| Engineering | `192.168.1.0` | `/26` | Department LAN |
| HR | `192.168.1.64` | `/27` | Department LAN |
| Sales | `192.168.1.96` | `/27` | Department LAN |
| Branch | `192.168.1.128` | `/27` | Remote office LAN |
| Server farm | `192.168.1.160` | `/28` | Central services |
| Management | `192.168.1.176` | `/29` | Network management |

The Branch LAN uses `192.168.1.129/27` as its router-side gateway address. Refer to the Packet Tracer configuration for the complete interface, VLAN, WAN, and IPv6 addressing assignments.

## Implementation Highlights

### VLAN Segmentation and Inter-VLAN Routing

Departmental traffic is separated using VLANs and 802.1Q trunk connections. Layer 3 routing enables communication between permitted subnets. The design also includes management and native/unused VLAN considerations.

### Dynamic Routing with OSPF

OSPF is used to exchange routes between the enterprise routers, including the branch. Neighbor adjacencies and learned routes can be checked with `show ip ospf neighbor` and `show ip route`.

### Centralized DHCP

DHCP provides dynamic IPv4 configuration for clients across multiple networks. Router DHCP relay (`ip helper-address`) forwards requests from remote VLANs to the central DHCP server.

### NAT/PAT and External Connectivity

The edge-router design uses NAT overload to translate multiple private IPv4 client addresses to an ISP-facing interface address for communication with a **simulated external server**. Final translation-table and end-to-end connectivity evidence should be captured from the finished topology.

### IPv6 / Dual Stack

IPv6 addressing and dual-stack connectivity are part of the assignment scope. Verify configured IPv6 interfaces, routes, and successful IPv6 pings before describing this section as fully implemented.

### Security and Wireless

The project considers switch port security, DHCP snooping, BPDU Guard, and wireless client connectivity. Check the final device configurations for the exact controls enabled and their test results.

## Verification Commands

Run the appropriate commands in the Packet Tracer device CLI:

```text
show ip interface brief
show vlan brief
show interfaces trunk
show ip route
show ip ospf neighbor
show ip protocols
show ip nat translations
show ip nat statistics
show ipv6 interface brief
show ipv6 route
show port-security
show ip dhcp snooping
```

On a client PC, use `ipconfig` and `ping <destination-ip>` to check DHCP assignment and reachability. Some commands are device-specific and may not be available on every Packet Tracer model.

## How to Run

1. Install **Cisco Packet Tracer**.
2. Clone or download this repository.
3. Open the included `.pkt` project file in Packet Tracer.
4. Allow the simulation to converge and DHCP clients to acquire addresses.
5. Inspect router/switch configurations and test connectivity from the PCs.
6. Review the screenshots and report for documented configuration and test evidence.

## Suggested Repository Structure

```text
enterprise-network-design/
├── README.md
├── packet-tracer/
│   └── enterprise-network.pkt
├── screenshots/
│   ├── network-topology.png
│   ├── vlan-and-trunks.png
│   ├── dhcp-verification.png
│   ├── ospf-routing.png
│   ├── nat-pat-verification.png
│   └── ipv6-verification.png
└── docs/
    └── project-report.pdf
```

*The paths above are a suggested layout. Add your actual `.pkt` file, original screenshots, and your own report; remove any entries you do not provide.*

## Learning Outcomes

- Plan an enterprise IPv4 addressing scheme using VLSM.
- Configure and troubleshoot VLANs, trunks, routing, and DHCP relay.
- Understand multi-area OSPF and remote-branch connectivity.
- Explore NAT/PAT, IPv6, wireless networking, and Layer 2 security.
- Validate a network using IOS diagnostic commands and end-to-end tests.

## Notes

This repository documents an **educational network simulation**. The ISP and external services are simulated; connectivity tests do not demonstrate real-world Internet access. Replace sample screenshots and filenames with evidence from the final project. Do not upload passwords, secrets, or other private information.

## Author

**[Your Name]**  
Enterprise Networking Assignment  
**[University / Course]**
