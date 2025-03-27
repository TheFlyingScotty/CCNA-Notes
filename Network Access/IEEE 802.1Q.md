Related: [[VLAN]], [[Trunk Ports]]

Definition:
IEEE 802.1Q is a networking standard that supports virtual LANs (VLANs) on an Ethernet network. It defines a method for tagging Ethernet frames with VLAN information, allowing multiple VLANs to coexist on a single physical network. This standard is commonly referred to as "dot1q."

Explanation:
IEEE 802.1Q works by inserting a 4-byte VLAN tag into the Ethernet frame header. This tag includes a VLAN identifier (VID) that specifies the VLAN to which the frame belongs. When a switch receives a tagged frame, it uses the VID to determine the appropriate VLAN and forwards the frame accordingly. This tagging mechanism enables VLANs to span multiple switches and allows for VLAN traffic to be carried over trunk links between switches.

Use Cases:
1. **Inter-Switch VLAN Communication**:
   - IEEE 802.1Q is used to enable VLAN communication between switches. By tagging frames with VLAN information, switches can forward traffic for multiple VLANs over a single trunk link. This is essential for maintaining VLAN segmentation across a network with multiple switches.

1. [[Router on a stick]]:
   - In a "Router on a Stick" configuration, IEEE 802.1Q is used to tag frames on subinterfaces of a router. This allows the router to route traffic between different VLANs using a single physical interface. Each subinterface is associated with a specific VLAN and uses 802.1Q tagging to identify VLAN traffic.

3. **Network Segmentation**:
   - IEEE 802.1Q is used to segment network traffic into different VLANs for security, performance, and management purposes. For example, separating guest traffic from internal traffic, or isolating different departments within an organization. VLAN tagging ensures that traffic remains isolated and only reaches the intended VLAN.

4. **Service Provider Networks**:
   - Service providers use IEEE 802.1Q to deliver multiple customer VLANs over a shared infrastructure. This allows them to provide VLAN-based services to multiple customers while maintaining traffic separation and security.

Command to Configure IEEE 802.1Q Trunking on a Switch:
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
exit

Summary:
- **IEEE 802.1Q**: A standard for VLAN tagging on Ethernet networks, allowing multiple VLANs to coexist on a single physical network.
- **Use Cases**: Inter-switch VLAN communication, "Router on a Stick" configurations, network segmentation, and service provider networks.