Related, [[VLAN]]

Definition of VLAN Leaking:
VLAN leaking, also known as VLAN hopping, is a network security vulnerability where traffic from one VLAN can be accessed or intercepted by devices in another VLAN. This can occur due to misconfigurations or exploitation of certain network protocols, leading to unauthorized access to VLAN traffic.

Explanation:
VLAN leaking typically happens in two main scenarios:

1. Switch Spoofing:
   - In switch spoofing, an attacker configures a device to act as a switch and negotiates a trunk link with a legitimate switch using Dynamic Trunking Protocol (DTP). Once the trunk link is established, the attacker can send and receive traffic from multiple VLANs, bypassing VLAN segmentation.

2. Double Tagging:
   - In double tagging, an attacker sends frames with two VLAN tags. The first tag is stripped off by the first switch, and the frame is forwarded to the next switch with the second tag still intact. This can cause the frame to be forwarded to a different VLAN than intended, allowing the attacker to access traffic from another VLAN.

Use Cases and Implications:
1. Security Breach:
   - VLAN leaking can lead to unauthorized access to sensitive data and resources. Attackers can intercept traffic, perform man-in-the-middle attacks, or gain access to restricted network segments.

2. Network Segmentation Failure:
   - VLAN leaking undermines the purpose of VLANs, which is to segment network traffic for security, performance, and management reasons. It can lead to data breaches and compromise the integrity of the network.

3. Mitigation Strategies:
   - Disable Unused Ports: Disable all unused switch ports to prevent unauthorized devices from connecting to the network.
   - Disable DTP: Configure switch ports to not negotiate trunking automatically by setting them to access mode or using the `switchport nonegotiate` command.
   - Use VLAN Access Control Lists (VACLs): Implement VACLs to control and filter traffic between VLANs.
   - Implement Port Security: Use port security features to limit the number of devices that can connect to a switch port and to restrict MAC addresses.
   - Double Tagging Protection: Ensure that the native VLAN is different from the VLANs used for sensitive data and that it is not used for any other purpose.

Example Configuration to Prevent VLAN Leaking:
1. Disable DTP on Access Ports:
   configure terminal
   interface range GigabitEthernet0/1 - 24
   switchport mode access
   switchport nonegotiate
   exit

2. Set Native VLAN to an Unused VLAN:
   configure terminal
   interface GigabitEthernet0/1
   switchport trunk native vlan 999
   exit

3. Implement Port Security:
   configure terminal
   interface GigabitEthernet0/1
   switchport port-security
   switchport port-security maximum 2
   switchport port-security violation restrict
   switchport port-security mac-address sticky
   exit

Summary:
- VLAN Leaking: A security vulnerability where traffic from one VLAN can be accessed by devices in another VLAN.
- Causes: Typically occurs due to switch spoofing or double tagging attacks.
- Implications: Can lead to unauthorized access, data breaches, and compromised network segmentation.
- Mitigation: Disable unused ports, disable DTP, use VACLs, implement port security, and protect against double tagging.