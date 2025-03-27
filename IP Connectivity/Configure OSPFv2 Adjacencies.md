
Related: [[OSPF]]
Before routers in an Open Shortest Path First (OSPF) area can exchange information, they must establish a neighbor relationship, which is also known as an adjacency. An OSPF router that has not yet exchanged information with a potential neighbor is considered to be in the Down neighbor state. OSPF routers establish adjacencies by sending Hello packets. 

# OSPF Process ID 
The OSPF process id is locally significant on the router. Unlike EIGRP for example, the process id does not have to match between 2 neighbors for a neigborship to establish.

You can run multiple OSPF processes on the same physical router and the process id would be how the router distinguishes between the processes. Also when redistributing OSPF into another routing protocol you need to specify the process id.

Note that running multiple OSPF processes on the same router is not normally recommended as OSPF can be quite heavy on the router rseources.

# Enabling OSPF
To enable OSPF on a router, you should issue the *router ospf process-id* command from global configuration mode, where process-id is any positive integer in the range from 1 through 65,535 that identifies the routing process. The OSPF process ID does not have to match across routers in an area, because the process ID is locally significant to the router. After you have enabled OSPF, you will be placed into router configuration mode, as indicated by the Router1(config-router)# prompt.

# Configuring an Interface to Operate in OSPF

To configure an Interface to Operate in OSPF you need to go into the Interface Configuration mode *INT FA0/0* then issue the command (*ip ospf "Process-ID" area "OSPF AREA"*) For example :    *ip ospf 10 area 0*

# Configuring a Network to Operate in OSPF

Configuring a network in OSPF can make specific interfaces that are configured with that network participate in OSPF. The way you would do that is by using the router configuration mode i.e using the (*router ospf 10*) command, then using the **network** command which is *network "ip-address" "Wildcard" area "Area-id"*  An example is below:
	- network 203.0.113.0 0.0.0.7 area 0
		- By using the wildcard mask of 0.0.0.7 to configure Router1 to advertise the 203.0.113.0 network in OSPF, you have configured Router1 to advertise the 203.0.113.0/29 network, which encompasses the range of host IP addresses from 203.0.113.1 through 203.0.113.6. The [[Wildcard mask]] of 0.0.0.7 is the equivalent of a [[subnet]] mask of 255.255.255.248.  
		- The OSPF network command can thus be configured to advertise both the 203.0.113.0/30 network that is configured on the Serial 0/0 interface and the 203.0.113.4/30 network that is configured on the FastEthernet 0/0 interface by using a single command, even though the [[Wildcard mask]] you issued with the network command is not equivalent to the [[subnet]] mask that is configured on each interface.


# How to show the OSPF router process section of the running configuration && what criteria is needed for OSPF routers to form adjacency

On both Router1 and Router2, you should issue the following commands to display the OSPF router process section of the running configuration:  
  
On Router1:Router1(config-router)#end  
Router1#show running-config | section router  
router ospf 10  
log-adjacency-changes  
network 203.0.113.0 0.0.0.7 area 0  
  
On Router2:Router2(config-router)#end  
Router2#show running-config | section router  
router ospf 20  
log-adjacency-changes  
network 203.0.113.0 0.0.0.3 area 0  

Based on the output, you can determine that the OSPF process ID and the wildcard mask configured with the network commands differ between routers. Neither of these criteria need match for OSPF routers to form an adjacency. By contrast, all of the following must match:  
  

- Hello timer
- dead timer
- OSPF area
- OSPF authentication credentials, if configured


# OSPF Router ID explained

The OSPF router ID is used to uniquely identify each router on the network. You can manually configure a router ID for a router by issuing the router-id ip-address command in router configuration mode, where ip-address is the address that you want OSPF to acknowledge as the new router ID. If you manually configure a router ID, it is important to ensure that the router ID is unique to a given OSPF router on the network. **Two OSPF routers that have the same router ID will not be able to form an adjacency.**
  
If you do not manually configure a router ID, then the router ID will be the highest IP address configured among loopback interfaces on the router. If no loopback addresses are configured on the router, the router ID will be the highest IP address configured among all physical interfaces on the router.  
  
**Cisco recommends using a loopback interface instead of a physical interface for the router ID. Because a loopback interface is never in the down state, OSPF is considered to be more stable when the router ID is configured from the IP address of a loopback interface.**  
  
You can verify the router ID that has been assigned to an OSPF router by issuing the do show ip ospf command in router configuration mode, as shown in the following output:
Router3(config-router)#do show ip ospf  
Routing Process "ospf 30" with ID 3.3.3.3  

# Verifying OSPF neighbor relationships and understanding the CLI output

You should issue the following commands to verify that the OSPF neighbor relationships on each router are up and in the FULL state:  
  
On Router1:Router1#show ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
3.3.3.3 1 FULL/DR 00:00:30 203.0.113.6 FastEthernet0/0  
2.2.2.2 0 FULL/ - 00:00:30 203.0.113.2 Serial0/0  
  
On Router2:Router2(config-router)#end  
Router2#show ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
1.1.1.1 0 FULL/ - 00:00:39 203.0.113.1 Serial0/0  
  
On Router3:Router3(config-router)#end  
Router3(config)#show ip ospf neighbor  
Neighbor ID Pri State Dead Time Address Interface  
1.1.1.1 1 FULL/BDR 00:00:33 203.0.113.5 FastEthernet0/0  


Based on the output, you can determine that each neighbor relationship is in the FULL state. Once a neighbor adjacency has been established by the exchange of Hello packets, OSPF sends a series of four other packets in order to establish or synchronize the OSPF link-state database (LSDB). The router relationships will thus proceed through the following states after an adjacency is established:  
  
  

- ExStart
- Loading
- Full or two-way

  
  
Neighbors that are stuck in the ExStart state and never transition to FULL or 2WAY in the show ip ospf neighbor output might have mismatched maximum transmission unit (MTU) values.  
  
The FULL state is the normal state for the OSPF designated router (DR) and backup designated router (BDR) and their neighbors. Other OSPF neighbors remain in the 2WAY state. In this scenario, only the relationship between Router1 and Router3 results in a DR and BDR election. This is because router elections for DR and BDR are only performed on broadcast multiaccess networks. Point-to-point networks, like the one connecting Router1 to Router2, do not perform these elections.  
  
OSPF uses the router ID and the priority value to elect the DR and BDR for an OSPF multiaccess network segment. OSPF routers in each multiaccess network elect a DR and a BDR. The DR generates link-state advertisements (LSAs) that contain OSPF routing information, and the BDR takes over for the DR if the DR fails. Because only the DR and BDR generate LSAs, network bandwidth is conserved.  
  
The DR is typically the router with the highest OSPF priority, and the BDR is typically the router with the second-highest OSPF priority. If priorities are equal between two or more routers, the router with the highest router ID will typically be elected to become the DR. By default, OSPF interfaces have a priority value of 1, although this value can be manually configured to any decimal value in the range from 0 through 255. Manually configuring a value of 0 will prevent a router from becoming the DR.




