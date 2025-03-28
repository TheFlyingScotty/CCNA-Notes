
Related: [[Port Address Translation (PAT) (also called NAT Overload)]],[[access control lists (ACL)]]
Implementing Port Address Translation (PAT):

Port Address Translation (PAT), also known as NAT Overload, allows multiple devices on a private network to share a single public IP address by using unique port numbers. Below are the steps and commands to configure PAT on a Cisco router.

1. Enter Global Configuration Mode:
   Command:
   configure terminal
   Explanation:
   This command puts the router into global configuration mode, allowing you to make configuration changes.

2. Define the Access List for Private IPs:
   Command:
   access-list <access-list-number> permit <private-ip-subnet> <wildcard-mask>
   Example:
   access-list 1 permit 192.168.1.0 0.0.0.255
   Explanation:
   This command creates an access list (numbered 1) that permits traffic from the private IP subnet 192.168.1.0/24. The wildcard mask 0.0.0.255 specifies the range of IPs in the subnet.

3. Configure PAT Using the Public IP Address:
   Command:
   ip nat inside source list <access-list-number> interface <interface-id> overload
   Example:
   ip nat inside source list 1 interface GigabitEthernet0/1 overload
   Explanation:
   This command enables PAT by linking the access list (1) to the public interface (GigabitEthernet0/1). The keyword "overload" allows multiple private IPs to share the same public IP by using unique port numbers.

4. Identify the Inside Interface:
   Command:
   interface <interface-id>
   ip nat inside
   Example:
   interface GigabitEthernet0/0
   ip nat inside
   Explanation:
   This command specifies the interface connected to the private network (e.g., GigabitEthernet0/0) as the "inside" NAT interface. Traffic originating from this interface will be translated.

5. Identify the Outside Interface:
   Command:
   interface <interface-id>
   ip nat outside
   Example:
   interface GigabitEthernet0/1
   ip nat outside
   Explanation:
   This command specifies the interface connected to the public network (e.g., GigabitEthernet0/1) as the "outside" NAT interface. Traffic destined for the public network will be translated.

6. Save the Configuration:
   Command:
   write memory
   Explanation:
   This command saves the configuration to the router's startup configuration, ensuring the NAT settings persist after a reboot.

Complete Example Configuration:
Suppose you want to translate private IPs in the range 192.168.1.0/24 to a single public IP address on the interface GigabitEthernet0/1. The private network is connected to GigabitEthernet0/0.

Commands:
configure terminal
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 interface GigabitEthernet0/1 overload
interface GigabitEthernet0/0
ip nat inside
exit
interface GigabitEthernet0/1
ip nat outside
exit
write memory

Verification:
After configuring PAT, you can verify the NAT settings using the following command:
show ip nat translations
Explanation:
This command displays the NAT translation table, showing the mappings between private IPs, public IPs, and port numbers.

Summary:
- PAT Command: ip nat inside source list <access-list-number> interface <interface-id> overload
- Inside Interface: Mark the interface connected to the private network as ip nat inside.
- Outside Interface: Mark the interface connected to the public network as ip nat outside.
- Purpose: PAT allows multiple private IPs to share a single public IP by using unique port numbers, conserving public IP addresses.