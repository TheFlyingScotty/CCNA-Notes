Related:[[access control lists (ACL)]]

Definition:  
Extended Access Control Lists (Extended ACLs) are a set of rules used on network devices to filter traffic based on multiple criteria, such as source and destination IP addresses, protocols (e.g., TCP, UDP, ICMP), and port numbers. They provide more granular control over traffic compared to standard ACLs.

Explanation:  
Extended ACLs operate at Layer 3 (Network) and Layer 4 (Transport) of the OSI model. They allow administrators to permit or deny traffic based on detailed parameters, making them ideal for securing networks and controlling specific types of traffic. Extended ACLs can be applied to interfaces in either inbound or outbound directions.

Key Features:

1. Granular Filtering:
    - Filters traffic based on source and destination IP addresses, protocols, and port numbers.
2. Protocol-Specific:
    - Supports filtering for specific protocols like TCP, UDP, ICMP, and others.
3. Flexible Placement:
    - Typically placed close to the source of traffic to reduce unnecessary network load.
4. Numbered or Named:
    - Can be identified by numbers (100-199, 2000-2699) or names for easier management.

Use Cases:

1. Traffic Filtering:
    - Block or allow specific traffic, such as permitting SSH traffic but denying Telnet traffic.
2. Security:
    - Restrict access to sensitive parts of the network by filtering traffic based on IP and port.
3. Quality of Service (QoS):
    - Identify specific traffic types for prioritization or shaping.

Example:  
To block HTTP traffic (port 80) from the source IP 192.168.1.0/24 to the destination IP 10.0.0.0/24:

1. Create the ACL:  
    access-list 100 deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80  
    access-list 100 permit ip any any
    
    - The first line denies HTTP traffic from 192.168.1.0/24 to 10.0.0.0/24.
    - The second line permits all other traffic.
2. Apply the ACL to an interface:  
    interface GigabitEthernet0/0  
    ip access-group 100 in
    
    - This applies the ACL to inbound traffic on the specified interface.

Summary:  
Extended ACLs provide detailed traffic filtering based on multiple criteria, making them essential for securing networks, controlling traffic, and implementing policies. They are more versatile than standard ACLs and are widely used in enterprise networks.