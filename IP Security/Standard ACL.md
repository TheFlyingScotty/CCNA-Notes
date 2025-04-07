Related: [[access control lists (ACL)]]
Definition:  
Standard Access Control Lists (Standard ACLs) are a set of rules used on network devices to filter traffic based solely on the source IP address. They provide basic traffic filtering by permitting or denying packets from specific IP addresses or subnets.

Explanation:  
Standard ACLs operate at Layer 3 (Network) of the OSI model. They are simpler than Extended ACLs and do not consider destination IP addresses, protocols, or port numbers. Standard ACLs are typically applied close to the destination to avoid unnecessarily blocking traffic from other sources.

Key Features:

1. Source-Based Filtering:
    - Filters traffic based only on the source IP address.
2. Simplicity:
    - Easier to configure and manage compared to Extended ACLs.
3. Numbered or Named:
    - Can be identified by numbers (1-99, 1300-1999) or names for easier management.

Use Cases:

1. Basic Traffic Control:
    - Allow or block traffic from specific devices or subnets.
2. Security:
    - Restrict access to certain parts of the network based on the source IP address.

Example:  
To block traffic from the source IP 192.168.1.0/24:

1. Create the ACL:  
    access-list 10 deny 192.168.1.0 0.0.0.255  
    access-list 10 permit any
    
    - The first line denies traffic from 192.168.1.0/24.
    - The second line permits all other traffic.
2. Apply the ACL to an interface:  
    interface GigabitEthernet0/0  
    ip access-group 10 in
    
    - This applies the ACL to inbound traffic on the specified interface.

Summary:  
Standard ACLs provide basic traffic filtering based on the source IP address. They are simple to configure and are best suited for scenarios where detailed filtering is not required. However, they lack the granularity of Extended ACLs and are typically used for basic access control.