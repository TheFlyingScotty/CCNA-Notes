
Related: [[ Configure OSPFv2 Adjacencies]] ,[[Configure Point to Point OSPFv2]], [[OSPF Commands]], [[IP Connectivity]], [[OSPF Troubleshooting]]

# OSPF Process ID 
The OSPF process id is locally significant on the router. Unlike EIGRP for example, the process id does not have to match between 2 neighbors for a neighborship to establish.

You can run multiple OSPF processes on the same physical router and the process id would be how the router distinguishes between the processes. Also when redistributing OSPF into another routing protocol you need to specify the process id.

Note that running multiple OSPF processes on the same router is not normally recommended as OSPF can be quite heavy on the router resources.


# OSPF Router ID explained

The OSPF router ID is used to uniquely identify each router on the network. You can manually configure a router ID for a router by issuing the router-id ip-address command in router configuration mode, where ip-address is the address that you want OSPF to acknowledge as the new router ID. If you manually configure a router ID, it is important to ensure that the router ID is unique to a given OSPF router on the network. **Two OSPF routers that have the same router ID will not be able to form an adjacency.**
  
If you do not manually configure a router ID, then the router ID will be the highest IP address configured among loopback interfaces on the router. If no loopback addresses are configured on the router, the router ID will be the highest IP address configured among all physical interfaces on the router.  
  
**Cisco recommends using a loopback interface instead of a physical interface for the router ID. Because a loopback interface is never in the down state, OSPF is considered to be more stable when the router ID is configured from the IP address of a loopback interface.**  
  
You can verify the router ID that has been assigned to an OSPF router by issuing the do show ip ospf command in router configuration mode, as shown in the following output:
Router3(config-router)#do show ip ospf  
Routing Process "ospf 30" with ID 3.3.3.3  
# OSPF DR and BDR

**Definition**: In OSPF (Open Shortest Path First), the Designated Router (DR) and Backup Designated Router (BDR) are elected on broadcast and non-broadcast multi-access (NBMA) networks to reduce the number of adjacencies and minimize the amount of Link State Advertisement (LSA) traffic.

### How OSPF Elects DR and BDR

1. **Router Priority**:
    
    - Each OSPF router interface has a priority value (0-255). The default priority is 1.
    - The router with the highest priority on the network segment is elected as the DR.
    - The router with the second highest priority is elected as the BDR.
    - If a router's priority is set to 0, it is ineligible to become DR or BDR.
2. **Router ID**:
    
    - If there is a tie in priority, the router with the highest Router ID (RID) is elected as the DR.
    - The router with the second highest Router ID becomes the BDR.
    - The Router ID is typically the highest IP address on the router or can be manually set.
3. **Election Process**:
    
    - When OSPF routers on a network segment start up, they send Hello packets to discover other OSPF routers.
    - During the discovery process, routers exchange Hello packets containing their priority and Router ID.
    - Based on the priority and Router ID, the DR and BDR are elected.
    - The election process is non-preemptive, meaning once a DR and BDR are elected, they remain in their roles until they fail or are manually reset.

### Why OSPF Elects DR and BDR

1. **Reduce Adjacencies**:
    
    - On a broadcast or NBMA network, if every router formed an adjacency with every other router, the number of adjacencies would grow exponentially.
    - By electing a DR and BDR, each router only forms an adjacency with the DR and BDR, significantly reducing the number of adjacencies.
2. **Minimize LSA Traffic**:
    
    - The DR is responsible for generating and distributing LSAs on behalf of the network segment.
    - This reduces the amount of LSA traffic because only the DR sends LSAs to all other routers, rather than every router sending LSAs to every other router.

### Example Configuration

To influence the DR/BDR election, you can set the OSPF priority on an interface:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Enter Interface Configuration Mode**:
    
    Router(config)# interface GigabitEthernet0/0
    
3. **Set OSPF Priority**:
    
    Router(config-if)# ip ospf priority 100
    
4. **Exit Interface Configuration Mode**:
    
    Router(config-if)# exit
    
5. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### Verification

To verify the DR and BDR on a network segment, use the `show ip ospf neighbor` command:

Router# show ip ospf neighbor

The output will show the state of each neighbor, including which router is the DR and which is the BDR.

### Summary

- **DR and BDR Election**: Based on OSPF priority and Router ID.
- **Purpose**: Reduce the number of adjacencies and minimize LSA traffic.
- **Configuration**: Adjust OSPF priority to influence the election process.

# Link State advertisements 

# What Interface types does OSPF support?
 OSPF supports six interface types:  
  

- Broadcast
- Nonbroadcast multiaccess (NBMA)
- Point-to-point
- Point-to-multipoint
- Point-to-multipoint NBMA
- Loopback
-

# OSPF neighbors states

Once a neighbor adjacency has been established by the exchange of Hello packets, OSPF sends a series of four other packets in order to establish or synchronize the OSPF link-state database (LSDB). The router relationships will thus proceed through the following states after an adjacency is established:  
  

- ExStart
- Loading
- Full or two-way

  
Neighbors that are stuck in the ExStart state and never transition to FULL or 2WAY in the show ip ospf neighbor output might have mismatched maximum transmission unit (MTU) values.  
  
The FULL state is the normal state for the OSPF DR and BDR and their neighbors. Other OSPF neighbors remain in the 2WAY state. In this scenario, only the relationship between Router1 and Router3 results in a DR and BDR election. This is because router elections for DR and BDR are performed on broadcast multiaccess networks. Point-to-point networks, like the one connecting Router1 to Router2, do not perform these elections.  
  
OSPF uses the router ID and the priority value to elect the DR and BDR for an OSPF multiaccess network segment. OSPF routers in each multiaccess network elect a DR and a BDR. The DR generates link-state advertisements (LSAs) that contain OSPF routing information, and the BDR takes over for the DR if the DR fails. Because only the DR and BDR generate LSAs, network bandwidth is conserved.  
  
The DR is typically the router with the highest OSPF priority, and the BDR is typically the router with the second-highest OSPF priority. If priorities are equal between two or more routers, the router with the highest router ID will typically be elected to become the DR. By default, OSPF interfaces have a priority value of 1, although this value can be manually configured to any decimal value in the range from 0 through 255. Manually configuring a value of 0 will prevent a router from becoming the DR.


# How does OSPF calculate its composite metric
### How OSPF Calculates Its Metric

1. **Cost Calculation**:
    
    - The cost of an OSPF route is calculated based on the bandwidth of the links.
    - The formula used to calculate the cost is:
        
        Cost = Reference Bandwidth / Interface Bandwidth
        
    - The default reference bandwidth is 100 Mbps (100,000,000 bps).
2. **Interface Bandwidth**:
    
    - The bandwidth of the interface is used to calculate the cost.
    - For example, a FastEthernet interface with a bandwidth of 100 Mbps would have a cost of:
        
        Cost = 100,000,000 / 100,000,000 = 1
        
3. **Summing Costs**:
    
    - The total cost to reach a destination network is the sum of the costs of all the links along the path.
    - OSPF uses the Shortest Path First (SPF) algorithm, also known as Dijkstra's algorithm, to calculate the shortest path based on the cumulative cost.

### Example Calculation

Consider a network with the following topology:

Router A --(100 Mbps)--> Router B --(10 Mbps)--> Router C

1. **Cost of Link A-B**:
    
    - Bandwidth: 100 Mbps
    - Cost: `100,000,000 / 100,000,000 = 1`
2. **Cost of Link B-C**:
    
    - Bandwidth: 10 Mbps
    - Cost: `100,000,000 / 10,000,000 = 10`
3. **Total Cost from A to C**:
    
    - Cost of A-B: 1
    - Cost of B-C: 10
    - Total Cost: `1 + 10 = 11`

### Adjusting the Reference Bandwidth

The default reference bandwidth of 100 Mbps may not be suitable for modern high-speed networks. You can adjust the reference bandwidth to better reflect the network's capabilities.

1. **Enter OSPF Configuration Mode**:
    
    Router# configure terminal
    
    Router(config)# router ospf 1
    
2. **Set the Reference Bandwidth**:
    
    Router(config-router)# auto-cost reference-bandwidth 1000
    
    - This sets the reference bandwidth to 1000 Mbps (1 Gbps).

### Summary

- **OSPF Metric**: Calculated based on the bandwidth of the links.
- **Formula**: `Cost = Reference Bandwidth / Interface Bandwidth`
- **Default Reference Bandwidth**: 100 Mbps
- **Total Path Cost**: Sum of the costs of all links along the path.
- **SPF Algorithm**: Used to calculate the shortest path based on the cumulative cost.