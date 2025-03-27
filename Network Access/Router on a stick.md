Related: [[Network Access]]

Definition:
"Router on a Stick" is a network configuration in which a single physical router interface is used to route traffic between multiple VLANs on a network. This is achieved by configuring subinterfaces on the router, each associated with a different VLAN.

Explanation:
In a "Router on a Stick" configuration, a single physical interface on the router is divided into multiple logical subinterfaces. Each subinterface is assigned an IP address and is associated with a specific VLAN. The router uses these subinterfaces to route traffic between the VLANs. This setup allows inter-VLAN communication without the need for multiple physical interfaces on the router.

Use Cases:
1. **Small to Medium-Sized Networks**:
   - In small to medium-sized networks, "Router on a Stick" is an efficient way to enable inter-VLAN routing without requiring a Layer 3 switch. It reduces hardware costs by using a single router interface to handle traffic for multiple VLANs.

2. **Lab Environments**:
   - In lab environments or for testing purposes, "Router on a Stick" is a convenient way to simulate inter-VLAN routing. It allows network administrators and students to practice VLAN configuration and routing without needing extensive hardware.

3. **Network Segmentation**:
   - "Router on a Stick" is used to segment network traffic for security and performance reasons. By separating different types of traffic into VLANs (e.g., separating guest traffic from internal traffic), network administrators can control access and improve network performance.

Command to Configure "Router on a Stick":
1. Enter global configuration mode:
   configure terminal

2. Enter interface configuration mode for the physical interface:
   interface type number

3. Create a subinterface for each VLAN and assign an IP address:
   interface type number.subinterface
   encapsulation dot1Q vlan-id
   ip address ip-address subnet-mask

4. Repeat step 3 for each VLAN.

Example:
To configure "Router on a Stick" for VLANs 10 and 20 on interface GigabitEthernet0/1:

configure terminal
interface GigabitEthernet0/1.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit
interface GigabitEthernet0/1.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit

Summary:
- **"Router on a Stick"**: A network configuration using a single router interface with subinterfaces to route traffic between multiple VLANs.
- **Use Cases**: Suitable for small to medium-sized networks, lab environments, and network segmentation for security and performance.