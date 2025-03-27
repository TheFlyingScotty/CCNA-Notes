Related: [[Network Access]], [[Dynamic Trunking Protocol]]

Definition:
A trunk port is a switch port that is configured to carry traffic for multiple VLANs. Trunk ports use VLAN tagging to identify which VLAN each Ethernet frame belongs to, allowing VLAN traffic to be carried across the network.

Explanation:
Trunk ports are essential for inter-switch communication and for connecting switches to routers in a network with multiple VLANs. They use protocols such as [[IEEE 802.1Q]] to tag frames with VLAN information. This tagging enables the receiving switch or router to forward the frames to the appropriate VLAN. Trunk ports can carry traffic for multiple VLANs over a single physical link, making them efficient for network design.

[[Access ports]] vs Trunk ports:
Access ports are switch ports configured to carry traffic for a single VLAN, typically used to connect end devices like computers and printers. In contrast, trunk ports are switch ports configured to carry traffic for multiple VLANs, using VLAN tagging to identify and separate the traffic, and are typically used to connect switches to each other or to routers.

Use Case:
Trunk ports are used in scenarios where multiple VLANs need to be carried over a single link. For example, in a network with multiple switches, trunk ports can be used to connect the switches together, allowing VLAN traffic to flow between them. Trunk ports are also used to connect switches to routers in a router-on-a-stick configuration, where the router handles inter-VLAN routing. This setup is common in enterprise networks to ensure that VLAN traffic can traverse the entire network.

Command to Create Trunk Ports:
1. Enter global configuration mode:
   configure terminal

2. Enter interface configuration mode for the desired interface:
   interface type number

3. Set the interface to trunk mode:
   switchport mode trunk

4. (Optional) Specify the allowed VLANs on the trunk:
   switchport trunk allowed vlan vlan-list

Example:
To configure interface GigabitEthernet0/1 as a trunk port and allow VLANs 10, 20, and 30:

configure terminal
interface GigabitEthernet0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30