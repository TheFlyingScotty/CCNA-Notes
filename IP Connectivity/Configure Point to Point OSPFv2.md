Related: [[OSPF]]
A point-to-point leased line is one of the most common wide area network (WAN) connections. This type of connection uses a Serial interface to connect through a service provider to another Serial device at a remote location. Open Shortest Path First (OSPF) behaves differently over point-to-point links between routers than it does over point-to-multipoint or local area network (LAN) links.

### OSPF Behavior on Different Link Types

Open Shortest Path First (OSPF) is a link-state routing protocol that behaves differently depending on the type of link it is operating over. Here is a comparison of OSPF behavior over point-to-point links, point-to-multipoint links, and local area network (LAN) links.

### Point-to-Point Links

**Definition**: A point-to-point link connects exactly two routers.

**OSPF Behavior**:

- **No DR/BDR Election**: OSPF does not perform a Designated Router (DR) or Backup Designated Router (BDR) election on point-to-point links because there are only two routers.
- **Simplified Adjacency**: OSPF forms a full adjacency directly between the two routers.
- **LSA Exchange**: Link State Advertisements (LSAs) are exchanged directly between the two routers without the need for a DR/BDR.

**Example**:

Router(config)# interface Serial0/0

Router(config-if)# ip address 10.0.0.1 255.255.255.252

Router(config-if)# ip ospf network point-to-point

### Point-to-Multipoint Links

**Definition**: A point-to-multipoint link connects one router to multiple routers, but each connection is treated as a series of point-to-point links.

**OSPF Behavior**:

- **No DR/BDR Election**: Similar to point-to-point links, OSPF does not perform a DR/BDR election on point-to-multipoint links.
- **Direct Adjacencies**: OSPF forms direct adjacencies with each router in the point-to-multipoint network.
- **LSA Exchange**: LSAs are exchanged directly between the routers without the need for a DR/BDR.

**Example**:

Router(config)# interface Serial0/0

Router(config-if)# ip address 10.0.0.1 255.255.255.252

Router(config-if)# ip ospf network point-to-multipoint

### Local Area Network (LAN) Links

**Definition**: A LAN link connects multiple routers and hosts within the same broadcast domain, such as Ethernet.

**OSPF Behavior**:

- **DR/BDR Election**: OSPF performs a DR/BDR election to reduce the number of adjacencies and minimize LSA flooding. The DR is responsible for generating LSAs on behalf of the network, and the BDR takes over if the DR fails.
- **Adjacency Formation**: OSPF forms full adjacencies only with the DR and BDR. Other routers form 2-way adjacencies with each other.
- **LSA Exchange**: LSAs are exchanged through the DR and BDR, which then distribute the LSAs to other routers on the network.

**Example**:

Router(config)# interface GigabitEthernet0/0

Router(config-if)# ip address 192.168.1.1 255.255.255.0

Router(config-if)# ip ospf network broadcast

### Summary

- **Point-to-Point Links**: No DR/BDR election, direct adjacency between two routers.
- **Point-to-Multipoint Links**: No DR/BDR election, direct adjacencies with each router.
- **LAN Links**: DR/BDR election, full adjacencies with DR/BDR, 2-way adjacencies with other routers.

Understanding these differences helps in designing and troubleshooting OSPF networks, ensuring efficient and reliable routing.

