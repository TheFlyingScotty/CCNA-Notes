**ip ospf** *Process-id* **area** *area-id*
	-Places an interface in a specified OSPF process and area
	
**network** *network-address*  *[[Wildcard mask]]*  **area** *area-id*
	-activates OSPF on the specified network and places the matching interface in the specified area
	
**router ospf** *process-id*
	-enters router configuration mode for an OSPF process
	
**router-id** *ip-address*
	-  configures a 32-bit dotted-decimal OSPF router ID

**show ip interface brief**
	-  displays a summary of interfaces configured on the device
		- Example:
			Interface IP-Address OK? Method Status Protocol  
			FastEthernet0/0 203.0.113.1 YES manual up up  
			FastEthernet0/1 203.0.113.5 YES manual up up  
			GigabitEthernet0/0 unassigned YES unset administratively down down  
			GigabitEthernet0/1 unassigned YES unset administratively down down  
			GigabitEthernet0/2 unassigned YES unset administratively down down  
			Loopback0 172.16.0.1 YES manual up up  
			Loopback1 1.1.1.1 YES manual up up

**Show ip OSPF interface**  *{type number}* *{brief}*
	-displays OSPF interface information , can either be a specific interface or just leave it a brief
	
**show ip ospf** *{process-id} {area-id}* **neighbor**
	-displays OSPF neighbor information

**clear ip ospf process**
	- **Definition**: The `clear ip ospf process` command is used to reset the OSPF (Open Shortest Path First) routing process on a Cisco router. This command forces the router to restart the OSPF process, which can be useful for troubleshooting and reinitializing OSPF operations.
		- **Use Case** :
		- **Troubleshooting**: If you encounter issues with OSPF routing, such as stuck neighbor states or incorrect routing information, restarting the OSPF process can help resolve these issues.
		-**Configuration Changes**: After making significant changes to the OSPF configuration, restarting the OSPF process ensures that all routers in the OSPF domain reestablish their adjacencies and exchange updated routing information.
		- **Network Convergence**: In some cases, restarting the OSPF process can speed up network convergence by forcing routers to immediately reestablish adjacencies and recalculate routes.

**show ip ospf database**
	- **Definition**: The `show ip ospf database` command is used on Cisco routers to display the contents of the OSPF (Open Shortest Path First) link-state database. This database contains all the Link State Advertisements (LSAs) that the router has received from its OSPF neighbors. The command provides detailed information about the OSPF topology and is essential for troubleshooting and verifying OSPF operations.
		- **Use cases**:
		- **Troubleshooting**: Helps in diagnosing OSPF issues by providing detailed information about the LSAs in the OSPF database.
		-  **Verification**: Allows network administrators to verify that the OSPF topology is correctly formed and that all necessary LSAs are present.
		- **Network Analysis**: Provides insights into the OSPF network topology, including router links, network links, and external routes.
	

**ip ospf priority** *{Value}* 
	- The `ip ospf priority` command is used to set the OSPF (Open Shortest Path First) priority of an interface on a Cisco router. The priority value determines the likelihood of the router being elected as the Designated Router (DR) or Backup Designated Router (BDR) on a broadcast or non-broadcast multi-access (NBMA) network.
		- Example of the command would be using the value 10 to make a router become the dr


**show ip interface brief**
	- displays a brief summary of interface status and configuration

**Default-information originate**
	The `default-information originate` command is used in OSPF (Open Shortest Path First) to advertise a default route (0.0.0.0/0) to other OSPF routers. This command tells the OSPF process to generate and propagate a default route into the OSPF domain.
		-- use case
		**Default Route Advertisement**: When a router has a default route to an external network (e.g., the internet), it can use the `default-information originate` command to advertise this default route to other OSPF routers. This allows other routers in the OSPF domain to use this router as a gateway of last resort for destinations not covered by more specific routes.
			**Options**
			- **always**: Forces the router to advertise the default route even if it does not have a default route in its own routing table.
			- **metric <value>**: Sets the metric for the default route being advertised.
			- **metric-type <type>**: Sets the OSPF metric type for the default route. The type can be 1 or 2 (default is 2).
		    - **Type 1**: The cost is the sum of the external cost and the internal cost to reach the ASBR.
		    - **Type 2**: The cost is the external cost only.
			- **route-map <map-name>**: Specifies a route map to control the advertisement of the default route.
			-  default-information originate [always] [metric <value>] [metric-type <type>] [route-map <map-name>]

    


