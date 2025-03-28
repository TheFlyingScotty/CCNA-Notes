Related: [[Dynamic NAT]], [[access control lists (ACL)]]

Implementing Dynamic NAT:

Dynamic NAT maps private IP addresses to a pool of public IP addresses. Below are the steps and commands to configure Dynamic NAT on a Cisco router.

1. Enter Global Configuration Mode:
   Command:
   configure terminal
   Explanation:
   This command puts the router into global configuration mode, allowing you to make configuration changes.

2. Define the NAT Pool:
   Command:
   ip nat pool <pool-name> <start-public-ip> <end-public-ip> netmask <subnet-mask>
   Example:
   ip nat pool PUBLIC_POOL 203.0.113.5 203.0.113.10 netmask 255.255.255.248
   Explanation:
   This command creates a pool of public IP addresses named PUBLIC_POOL. The pool includes public IPs from 203.0.113.5 to 203.0.113.10 with a subnet mask of 255.255.255.248.

3. Define the [[access control lists (ACLs)]]access control lists (ACLs) for Private IPs:
   Command:
   access-list <access-list-number> permit <private-ip-subnet> <wildcard-mask>
   Example:
   access-list 1 permit 192.168.1.0 0.0.0.255
   Explanation:
   This command creates an access list (numbered 1) that permits traffic from the private IP subnet 192.168.1.0/24. The wildcard mask 0.0.0.255 specifies the range of IPs in the subnet.
4. [[access control lists (ACLs)]]
5. 

6. Link the Access List to the NAT Pool:
   Command:
   ip nat inside source list <access-list-number> pool <pool-name>
   Example:
   ip nat inside source list 1 pool PUBLIC_POOL
   Explanation:
   This command links the access list (1) to the NAT pool (PUBLIC_POOL). It tells the router to translate private IPs matching the access list to public IPs from the NAT pool.

5. Identify the Inside Interface:
   Command:
   interface <interface-id>
   ip nat inside
   Example:
   interface GigabitEthernet0/0
   ip nat inside
   Explanation:
   This command specifies the interface connected to the private network (e.g., GigabitEthernet0/0) as the "inside" NAT interface. Traffic originating from this interface will be translated.

6. Identify the Outside Interface:
   Command:
   interface <interface-id>
   ip nat outside
   Example:
   interface GigabitEthernet0/1
   ip nat outside
   Explanation:
   This command specifies the interface connected to the public network (e.g., GigabitEthernet0/1) as the "outside" NAT interface. Traffic destined for the public network will be translated.

7. Save the Configuration:
   Command:
   write memory
   Explanation:
   This command saves the configuration to the router's startup configuration, ensuring the NAT settings persist after a reboot.

Complete Example Configuration:
Suppose you want to translate private IPs in the range 192.168.1.0/24 to public IPs in the range 203.0.113.5 to 203.0.113.10. The private network is connected to GigabitEthernet0/0, and the public network is connected to GigabitEthernet0/1.

Commands:
configure terminal
ip nat pool PUBLIC_POOL 203.0.113.5 203.0.113.10 netmask 255.255.255.248
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 pool PUBLIC_POOL
interface GigabitEthernet0/0
ip nat inside
exit
interface GigabitEthernet0/1
ip nat outside
exit
write memory

Verification:
After configuring Dynamic NAT, you can verify the NAT settings using the following command:
show ip nat translations
Explanation:
This command displays the NAT translation table, showing the mappings between private and public IP addresses.

Summary:
- Dynamic NAT Command: ip nat inside source list <access-list-number> pool <pool-name>
- Inside Interface: Mark the interface connected to the private network as ip nat inside.
- Outside Interface: Mark the interface connected to the public network as ip nat outside.
- Purpose: Dynamic NAT dynamically maps private IPs to a pool of public IPs, allowing multiple devices to access the internet using a limited number of public IP addresses.