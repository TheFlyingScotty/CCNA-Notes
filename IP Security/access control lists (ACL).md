Related: [[Extended ACL]], [[Standard ACL]], [[Named ACL]], [[ACL Commands]], [[IP Security]]

Definition:
Access Control Lists (ACLs) are a set of rules used on network devices, such as routers and switches, to control and filter traffic based on various criteria. ACLs allow or deny traffic based on parameters such as source IP address, destination IP address, protocol, or port number.

Explanation:
ACLs operate at Layer 3 (IP) and Layer 4 (Transport) of the[[OSI model]] . They are used to enhance network security by controlling which traffic is allowed to pass through or is blocked. ACLs are applied to interfaces on a router or switch and can filter traffic in two directions:
- Inbound: Filters traffic entering an interface.
- Outbound: Filters traffic leaving an interface.

Types of ACLs:
1. Standard ACLs:
   - Filter traffic based only on the source IP address.
   - Use Case: Simple filtering, such as allowing or denying traffic from specific devices or subnets.
   - Example: access-list 1 permit 192.168.1.0 0.0.0.255

2. Extended ACLs:
   - Filter traffic based on multiple criteria, including source IP, destination IP, protocol (e.g., TCP, UDP, ICMP), and port numbers.
   - Use Case: Granular filtering, such as allowing HTTP traffic but blocking FTP traffic.
   - Example: access-list 100 permit tcp 192.168.1.0 0.0.0.255 any eq 80

3. Numbered ACLs:
   - Identified by a number (e.g., 1-99 for standard ACLs, 100-199 for extended ACLs).
   - Example: access-list 1 permit 192.168.1.0 0.0.0.255

4. Named ACLs:
   - Identified by a name instead of a number, allowing for easier management.
   - Example: ip access-list extended BLOCK_HTTP

Use Cases:
1. Traffic Filtering:
   - Block or allow specific traffic, such as denying access to a specific subnet or allowing only HTTP traffic.

2. Security:
   - Protect sensitive parts of the network by restricting access to certain devices or services.

3. Quality of Service (QoS):
   - Prioritize certain types of traffic by identifying them with ACLs.

1. [[NAT]] and VPNs:
   - Define which traffic should be translated or encrypted.

Example Configuration:
Suppose you want to block all traffic from the subnet 192.168.1.0/24 to the subnet 10.0.0.0/24.

Commands:
1. Create an extended ACL:
   access-list 100 deny ip 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255
   access-list 100 permit ip any any
   Explanation:
   - The first line denies all traffic from 192.168.1.0/24 to 10.0.0.0/24.
   - The second line permits all other traffic (important to avoid blocking all traffic).

2. Apply the ACL to an interface:
   interface GigabitEthernet0/0
   ip access-group 100 in
   Explanation:
   - This applies the ACL to inbound traffic on the GigabitEthernet0/0 interface.

Verification:
Use the following command to verify the ACL:
   show access-lists
Explanation:
This command displays the configured ACLs and their hit counts (how many packets matched each rule).

Summary:
- ACLs: A set of rules to filter traffic based on IP, protocol, or port.
- Types: Standard ACLs (source IP only) and Extended ACLs (source, destination, protocol, and port).
- Use Cases: Traffic filtering, security, QoS, NAT, and VPNs.
- Application: ACLs are applied to router or switch interfaces in inbound or outbound directions.