Related: [[Trunk Ports]], [[Access ports]], [[Network Access]],


Definition:
Dynamic Trunking Protocol (DTP) is a Cisco proprietary protocol used to negotiate trunking on a link between two switches and to automatically configure the trunking mode. DTP can dynamically establish a trunk link and manage the trunking configuration between switches.

Explanation:
DTP operates on Layer 2 and helps automate the process of configuring trunk links between switches. When DTP is enabled on a switch port, it can negotiate with the connected device to determine whether the link should be a trunk or an access link. DTP can operate in different modes, such as dynamic desirable, dynamic auto, trunk, and access. The protocol simplifies network administration by reducing the need for manual trunk configuration.

![[Pasted image 20250310152908.png]]

Dynamic Trunking Protocol (DTP) Modes:

1. Access Mode:
   - **Definition**: Configures the port as a non-trunking, access port.
   - **Use Case**: Used to connect end devices such as computers, printers, and IP phones to the network. The port will not negotiate trunking and will carry traffic for a single VLAN.
   - **Command**: switchport mode access

2. Trunk Mode:
   - **Definition**: Configures the port as a trunk port, carrying traffic for multiple VLANs.
   - **Use Case**: Used to connect switches to each other or to routers, allowing VLAN traffic to be carried across the network. The port will always operate as a trunk.
   - **Command**: switchport mode trunk

3. Dynamic Desirable Mode:
   - **Definition**: Actively attempts to convert the link to a trunk link. The port will initiate DTP negotiation to form a trunk link.
   - **Use Case**: Used when you want the port to actively try to establish a trunk link with the connected device. If the other side is set to trunk, dynamic desirable, or dynamic auto, a trunk link will be formed.
   - **Command**: switchport mode dynamic desirable

4. Dynamic Auto Mode:
   - **Definition**: Passively waits for the other side to initiate trunking. The port will form a trunk link if the other side is set to trunk or dynamic desirable.
   - **Use Case**: Used when you want the port to automatically form a trunk link if the connected device initiates it. This mode does not actively try to form a trunk link but will accept trunking if requested by the other side.
   - **Command**: switchport mode dynamic auto

1. Nonegotiate Mode:
   - **Definition**: Disables DTP on the port. The port will not send or respond to DTP frames.
   - **Use Case**: Used when you want to manually configure the port as a trunk or access port without using DTP. This mode is useful for security purposes to prevent unwanted trunking.
   - **Command**: switchport nonegotiate

Summary:
- **Access Mode**: Configures the port as an access port, carrying traffic for a single VLAN.
- **Trunk Mode**: Configures the port as a trunk port, carrying traffic for multiple VLANs.
- **Dynamic Desirable Mode**: Actively attempts to form a trunk link with the connected device.
- **Dynamic Auto Mode**: Passively waits for the other side to initiate trunking.
- **Nonegotiate Mode**: Disables DTP, requiring manual configuration of the port as a trunk or access port.

Use Case:
DTP is used in scenarios where network administrators want to automate the process of establishing trunk links between switches. For example, in a large enterprise network with multiple interconnected switches, DTP can be enabled to dynamically negotiate and establish trunk links, ensuring that VLAN traffic can flow between switches without manual intervention. This is particularly useful in environments where switches are frequently added or reconfigured.

Command to Create Dynamic Trunking Protocol:
1. Enter global configuration mode:
   configure terminal

2. Enter interface configuration mode for the desired interface:
   interface type number

3. Set the interface to use DTP in dynamic desirable mode:
   switchport mode dynamic desirable

Example:
To configure interface GigabitEthernet0/1 to use DTP in dynamic desirable mode:

configure terminal
interface GigabitEthernet0/1
switchport mode dynamic desirable