Related: [[VLAN]]
Definition:
A Switch Virtual Interface (SVI) is a virtual interface on a switch that provides Layer 3 routing capabilities for a VLAN. An SVI is used to enable inter-VLAN routing, allowing devices in different VLANs to communicate with each other through the switch.

Explanation:
SVIs are created on Layer 3 switches to provide IP addresses for VLANs and to enable routing between them. Each SVI is associated with a specific VLAN and is assigned an IP address that serves as the default gateway for devices in that VLAN. By configuring SVIs, a switch can perform routing functions, eliminating the need for an external router to handle inter-VLAN traffic. This simplifies network design and improves performance by keeping inter-VLAN traffic within the switch.

## Note:
	-To enable and configure SVI you must me in interface config mode, i.e use the command *int vlan 10* rather than *Vlan 10*

Use Case:
SVIs are used in scenarios where inter-VLAN routing is required. For example, in a corporate network with multiple VLANs for different departments (e.g., HR, Finance, IT), SVIs can be configured to enable communication between these VLANs. Each VLAN is assigned an SVI with an IP address, and the switch routes traffic between the VLANs. This setup is common in enterprise networks to provide efficient and scalable inter-VLAN routing.

Command to Create Switch Virtual Interface:
1. Enter global configuration mode:
   configure terminal

2. Create the SVI by entering interface configuration mode for the VLAN:
   interface vlan vlan-id

3. Assign an IP address and subnet mask to the SVI:
   ip address ip-address subnet-mask

4. Enable the SVI:
   no shutdown

Example:
To create an SVI for VLAN 10 with the IP address 192.168.10.1 and subnet mask 255.255.255.0:

configure terminal
interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shutdown