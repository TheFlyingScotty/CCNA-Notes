
Related: [[HSRP]], [[RIP]], [[EGP]]
## IP Routing Table

#### Below is an example of a Routing table
*Router1#show ip route*
*Codes: L - local, C - connected, S - static, I - IGRP, R - RIP, M - mobile, B - BGP*
       *D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area*
       *E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP*
       *i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, * - candidate default*
       *U - per-user static route*

*Gateway of last resort is 203.0.113.1 to network 0.0.0.0*

*S*   0.0.0.0/0 [1/0] via 203.0.113.1*
     *1.0.0.0/32 is subnetted, 1 subnets*
*C       1.1.1.1 is directly connected, Loopback0*
     *203.0.113.0/24 is variably subnetted, 2 subnets*
*C       203.0.113.0/30 is directly connected, Serial0/1*
*L       203.0.113.2/32 is directly connected, Serial0/1*
     *198.51.100.0/24 is variably subnetted, 2 subnets*
*C       198.51.100.0/29 is directly connected, FastEthernet1/0*
*L       198.51.100.1/32 is directly connected, FastEthernet1/0*

*00:00:30: %OSPF-5-ADJCHG: Process 1, Nbr 172.0.0.1 on Serial0/1 from LOADING to FULL, 

### 1. L - [[Local Route]]

**Definition**: Represents the IP address of the router's own interfaces. **Use Case**: Used to route traffic destined for the router itself. **Example**:

L 192.168.1.1/32 is directly connected, Loopback0

### 2. C - [[Connected Route]]

**Definition**: Represents networks directly connected to the router's interfaces. **Use Case**: Automatically added to the routing table when an interface is configured with an IP address and is up. **Example**:

C 192.168.1.0/24 is directly connected, FastEthernet0/0

### 3. S - [[Static Route]]

**Definition**: Manually configured routes by the network administrator. **Use Case**: Used for specific routing needs, such as routing traffic to a specific network or as a backup route. **Example**:

S 10.0.0.0/8 [1/0] via 192.168.1.2

### 4. I - [[IGRP]]

**Definition**: Routes learned through the Interior Gateway Routing Protocol (IGRP). **Use Case**: Used in older Cisco networks for routing within an autonomous system. **Example**:

I 172.16.0.0/16 [100/100] via 192.168.1.3, 00:00:10, FastEthernet0/1

### 5. R - [[RIP]]

**Definition**: Routes learned through the Routing Information Protocol (RIP). **Use Case**: Used in small to medium-sized networks for dynamic routing. **Example**:

R 192.168.2.0/24 [120/1] via 192.168.1.4, 00:00:30, FastEthernet0/2

### 6. M - Mobile

**Definition**: Routes learned through Mobile IP. **Use Case**: Used in networks that support mobile nodes. **Example**:

M 10.1.1.0/24 [1/0] via 192.168.1.5

### 7. B - BGP

**Definition**: Routes learned through the Border Gateway Protocol (BGP). **Use Case**: Used for routing between different autonomous systems on the internet. **Example**:

B 172.16.1.0/24 [20/0] via 192.168.1.6, 00:00:50, FastEthernet0/3

### 8. D - [[EIGRP]]

**Definition**: Routes learned through the Enhanced Interior Gateway Routing Protocol (EIGRP). **Use Case**: Used in Cisco networks for efficient and scalable routing within an autonomous system. **Example**:

D 192.168.3.0/24 [90/30720] via 192.168.1.7, 00:00:20, FastEthernet0/4

### 9. EX - EIGRP External

**Definition**: External routes learned through EIGRP. **Use Case**: Used for routes that are redistributed into EIGRP from another routing protocol. **Example**:

D EX 10.2.2.0/24 [170/30720] via 192.168.1.8, 00:00:40, FastEthernet0/5

### 10. O - [[OSPF]]

**Definition**: Routes learned through the Open Shortest Path First (OSPF) protocol. **Use Case**: Used for dynamic routing within an autonomous system. **Example**:

O 192.168.4.0/24 [110/2] via 192.168.1.9, 00:00:10, FastEthernet0/6

### 11. IA - OSPF Inter Area

**Definition**: Inter-area routes learned through OSPF. **Use Case**: Used for routes between different OSPF areas. **Example**:

O IA 10.3.3.0/24 [110/3] via 192.168.1.10, 00:00:30, FastEthernet0/7

### 12. E1 - OSPF External Type 1

**Definition**: External routes learned through OSPF with Type 1 metrics. **Use Case**: Used for routes redistributed into OSPF with external metrics. **Example**:

O E1 172.16.2.0/24 [110/20] via 192.168.1.11, 00:00:50, FastEthernet0/8

### 13. E2 - OSPF External Type 2

**Definition**: External routes learned through OSPF with Type 2 metrics. **Use Case**: Used for routes redistributed into OSPF with external metrics. **Example**:

O E2 172.16.3.0/24 [110/30] via 192.168.1.12, 00:01:00, FastEthernet0/9

### 14. E - [[EGP]]

**Definition**: Routes learned through the Exterior Gateway Protocol (EGP). **Use Case**: Used in older networks for routing between different autonomous systems. **Example**:

E 192.168.5.0/24 [140/1] via 192.168.1.13, 00:01:10, FastEthernet0/10

### 15. i - [[IS-IS]]

**Definition**: Routes learned through the Intermediate System to Intermediate System (IS-IS) protocol. **Use Case**: Used in large service provider networks for dynamic routing. **Example**:

i 192.168.6.0/24 [115/20] via 192.168.1.14, 00:01:20, FastEthernet0/11

### 16. L1 - IS-IS Level-1

**Definition**: Level-1 routes learned through IS-IS. **Use Case**: Used for routing within an IS-IS area. **Example**:

i L1 10.4.4.0/24 [115/30] via 192.168.1.15, 00:01:30, FastEthernet0/12

### 17. L2 - IS-IS Level-2

**Definition**: Level-2 routes learned through IS-IS. **Use Case**: Used for routing between IS-IS areas. **Example**:

i L2 10.5.5.0/24 [115/40] via 192.168.1.16, 00:01:40, FastEthernet0/13

### 18. * - Candidate Default

**Definition**: Indicates a candidate default route. **Use Case**: Used as a potential default route in the absence of a more specific route. **Example**:

* 0.0.0.0/0 [1/0] via 192.168.1.17

### 19. U - Per-User Static Route

**Definition**: Static routes configured on a per-user basis. **Use Case**: Used for specific user-defined routing needs. **Example**:

U 192.168.7.0/24 [1/0] via 192.168.1.18


First-Hop Redundancy Protocols (FHRPs) are technologies that provide router redundancy and high availability (HA) for Cisco networks. There are a number of different FHRPs, each of which differs in scalability and support among vendors. One Such FHRP is [[HSRP]]

