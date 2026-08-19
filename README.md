# Space City Architects — Enterprise Network Lab

![Space City Architects Phase 2 topology](docs/images/phase-2-topology.png)

## Project overview

This repository documents the design and staged implementation of a realistic two-site enterprise network for **Space City Architects**, a fictional architecture, engineering, and construction (AEC) firm. The lab is built in **Cisco Modeling Labs (CML) 2.10** and models a Houston headquarters, a branch office, internet/WAN connectivity, wired users, servers, guest devices, and wireless access.

The project is intentionally divided into phases so that the physical and logical design, configuration, validation, and troubleshooting can be reviewed independently. Phase 1 establishes the topology and an exact port-to-port cabling record before any device configuration is applied.

## Business requirements

- Provide resilient connectivity at Houston headquarters.
- Support corporate, server, administration, guest, and wireless endpoints.
- Connect the headquarters and branch through a simulated service provider.
- Use enterprise features such as VLANs, trunks, EtherChannel, first-hop redundancy, dynamic routing, DHCP, NAT, and access control in later phases.
- Produce documentation that another engineer could use to reproduce, validate, and troubleshoot the lab.

## Architecture highlights

- Two IOSvL2 core switches at headquarters.
- Two dual-homed IOSvL2 access switches at headquarters.
- Two links between the core switches reserved for a future LACP EtherChannel.
- Separate IOSv routers for the ISP, headquarters edge, and branch edge.
- A branch IOSvL2 access switch with wired and wireless endpoints.
- Native CML Wireless AP and Wireless Client nodes for wireless testing.
- GigabitEthernet interfaces on all routed and switched infrastructure links.

> CML host nodes retain their native interface names (`E0` for Desktop/Server nodes and `ens2` for Wireless AP nodes). Those names are correct for the selected node definitions and should not be renamed to GigabitEthernet.

## Lab inventory

| Site | Role | Nodes | CML node type |
| --- | --- | --- | --- |
| Internet/WAN | Service provider | `ISP` | IOSv |
| Houston HQ | WAN edge | `HQ-EDGE1` | IOSv |
| Houston HQ | Core | `HQ-CORE1`, `HQ-CORE2` | IOSvL2 |
| Houston HQ | Access | `HQ-ACCESS1`, `HQ-ACCESS2` | IOSvL2 |
| Houston HQ | Endpoints | `HQ-PC1`, `HQ-SERVER1`, `HQ-ADMIN1`, `HQ-GUEST1` | Desktop / Server |
| Houston HQ | Wireless | `HQ-AP1`, `HQ-AP2`, `HQ-WIFI1` | Wireless AP / Wireless Client |
| Branch | Router and access | `BR-R1`, `BR-ACCESS1` | IOSv / IOSvL2 |
| Branch | Endpoints | `BR-PC1`, `BR-AP1`, `BR-WIFI1` | Desktop / Wireless AP / Wireless Client |

## Project roadmap

| Phase | Scope | Status |
| --- | --- | --- |
| 1 | Topology, node selection, Gigabit interface allocation, and cabling documentation | Complete |
| 2 | Enterprise device initialization, hostnames, secure local access, SSH, and configuration standards | Complete |
| 3 | VLANs, management addressing, 802.1Q trunks, LACP EtherChannel, and spanning-tree tuning | Planned |
| 4 | Inter-VLAN routing, HSRP, WAN addressing, and OSPF | Planned |
| 5 | DHCP, NAT/PAT, ACLs, and wireless services | Planned |
| 6 | End-to-end validation, failure testing, hardening, and final documentation | Planned |

## Phase 1 deliverables

- [Phase 1 Method of Procedure](docs/phase-1-mop.md)
- [Clean topology diagram](docs/images/phase-1-topology.png)
- [Interface-labeled cabling diagram](docs/images/phase-1-interface-map.png)
- [CML export guidance](lab/README.md)

Phase 1 is a design and cabling milestone only. The nodes were not started and no Cisco IOS configuration commands were entered during this phase.

## Phase 2 deliverables

- [Phase 2 Method of Procedure](docs/phase-2-mop.md)
- [Phase 2 milestone topology](docs/images/phase-2-topology.png)
- [HQ edge administrative-access verification](docs/images/phase-2-hq-edge1-access-verification.png)
- [HQ edge SSH and login-control verification](docs/images/phase-2-hq-edge1-ssh-verification.png)

Phase 2 establishes a repeatable administrative baseline on the seven Space City Architects-managed routers and switches. The simulated `ISP` is retained as a provider-managed device and is excluded from the enterprise baseline. Management addressing and remote SSH reachability are intentionally deferred to Phase 3.

## Repository structure

```text
space-city-architects-network-lab/
├── README.md
├── docs/
│   ├── phase-1-mop.md
│   ├── phase-2-mop.md
│   └── images/
│       ├── phase-1-interface-map.png
│       ├── phase-1-topology.png
│       ├── phase-2-hq-edge1-access-verification.png
│       ├── phase-2-hq-edge1-ssh-verification.png
│       └── phase-2-topology.png
└── lab/
    └── README.md
```

## Skills demonstrated

- Translating business requirements into a layered network design.
- Selecting appropriate Cisco CML node types.
- Planning redundant uplinks and a future LACP bundle.
- Maintaining a deterministic interface map.
- Separating implementation into controlled, reviewable phases.
- Producing reproducible technical documentation and validation criteria.

## Disclaimer

Space City Architects is a fictional organization created for this lab. Cisco CML virtual interface names and forwarding performance model control-plane behavior; they are not claims of physical appliance throughput.
