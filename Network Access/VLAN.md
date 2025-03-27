Related: [[Network Access]],[[SVI]], [[VLAN Leaking]]

Definition:
A VLAN (Virtual Local Area Network) is a logical grouping of devices on a network that are segmented by function, team, or application, regardless of their physical location. VLANs allow network administrators to partition a single physical network into multiple distinct broadcast domains.

Explanation:
VLANs are used to improve network efficiency and security by segmenting traffic. Each VLAN is treated as a separate subnet, and devices within the same VLAN can communicate with each other as if they were on the same physical network. VLANs reduce broadcast traffic and can enhance security by isolating sensitive data and devices from the rest of the network. VLANs are configured on network switches, and each VLAN is identified by a unique VLAN ID.

Use Case:
VLANs are used in various scenarios to segment network traffic. For example, in an office environment, different departments such as HR, Finance, and IT can be assigned to separate VLANs to ensure that broadcast traffic is contained within each department and to enhance security by isolating sensitive data. VLANs are also used to separate guest traffic from internal traffic in a corporate network, ensuring that guests have limited access to network resources.

Command to Create VLAN:
1. Enter global configuration mode:
   configure terminal

2. Create the VLAN and assign a VLAN ID:
   vlan vlan-id

3. (Optional) Assign a name to the VLAN:
   name vlan-name

Example:
To create VLAN 10 and assign it the name "HR":

configure terminal
vlan 10
name HR