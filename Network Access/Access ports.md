Related: [[Network Access]]
Definition:
An access port is a switch port that is configured to carry traffic for a single VLAN. Access ports are typically used to connect end devices such as computers, printers, and IP phones to the network.

Explanation:
Access ports are configured to be part of a specific VLAN. When a device is connected to an access port, it can communicate with other devices in the same VLAN. Access ports do not tag Ethernet frames with VLAN information; they simply forward frames to the assigned VLAN. This makes access ports ideal for connecting end devices that do not need to be aware of VLAN tagging.

Definition Access ports vs [[Trunk Ports]]:
Access ports are switch ports configured to carry traffic for a single VLAN, typically used to connect end devices like computers and printers. In contrast, trunk ports are switch ports configured to carry traffic for multiple VLANs, using VLAN tagging to identify and separate the traffic, and are typically used to connect switches to each other or to routers.

Use Case:
Access ports are used in scenarios where end devices need to be connected to a specific VLAN. For example, in an office environment, computers on the same floor might be assigned to VLAN 10. Each computer would be connected to an access port configured for VLAN 10. This ensures that all computers on that floor can communicate with each other and access network resources assigned to VLAN 10.

Command to Create Access Ports:
1. Enter global configuration mode:
   configure terminal

2. Enter interface configuration mode for the desired interface:
   interface type number

3. Set the interface to access mode:
   switchport mode access

4. Assign the interface to a VLAN:
   switchport access vlan vlan-id

Example:
To configure interface GigabitEthernet0/1 as an access port for VLAN 10:

configure terminal
interface GigabitEthernet0/1
switchport mode access
switchport access vlan 10

Benefit of manually configuring a port to be access port only?
	- One benefit to manually configuring a port as an access port is that the port will no longer attempt to negotiate a trunk. Therefore, if a malicious actor were to connect a rogue switch to that port, the switch would not become capable of participating on the network as a switch.