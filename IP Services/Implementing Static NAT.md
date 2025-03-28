
Related: [[Static NAT]], [[IP Services Commands]]
Implementing Static NAT:

Static NAT maps a single private IP address to a single public IP address. Below are the steps and commands to configure Static NAT on a Cisco router.

1. Enter Global Configuration Mode:
   Command:
   configure terminal
   Explanation:
   This command puts the router into global configuration mode, allowing you to make configuration changes.

2. Define the Static NAT Mapping:
   Command:
   ip nat inside source static <private-ip> <public-ip>
   Example:
   ip nat inside source static 192.168.1.10 203.0.113.5
   Explanation:
   This command creates a one-to-one mapping between the private IP address (192.168.1.10) and the public IP address (203.0.113.5). Traffic from the private IP will appear to come from the public IP when accessing the internet, and traffic to the public IP will be forwarded to the private IP.

3. Identify the Inside Interface:
   Command:
   interface <interface-id>
   ip nat inside
   Example:
   interface GigabitEthernet0/0
   ip nat inside
   Explanation:
   This command specifies the interface connected to the private network (e.g., GigabitEthernet0/0) as the "inside" NAT interface. Traffic originating from this interface will be translated.

4. Identify the Outside Interface:
   Command:
   interface <interface-id>
   ip nat outside
   Example:
   interface GigabitEthernet0/1
   ip nat outside
   Explanation:
   This command specifies the interface connected to the public network (e.g., GigabitEthernet0/1) as the "outside" NAT interface. Traffic destined for the public IP will be translated and forwarded to the private IP.

5. Save the Configuration:
   Command:
   write memory
   Explanation:
   This command saves the configuration to the router's startup configuration, ensuring the NAT settings persist after a reboot.

Complete Example Configuration:
Suppose you want to map the private IP 192.168.1.10 to the public IP 203.0.113.5. The private network is connected to GigabitEthernet0/0, and the public network is connected to GigabitEthernet0/1.

Commands:
configure terminal
ip nat inside source static 192.168.1.10 203.0.113.5
interface GigabitEthernet0/0
ip nat inside
exit
interface GigabitEthernet0/1
ip nat outside
exit
write memory

Verification:
After configuring Static NAT, you can verify the NAT settings using the following command:
show ip nat translations
Explanation:
This command displays the NAT translation table, showing the mapping between private and public IP addresses.

Summary:
- Static NAT Command: ip nat inside source static <private-ip> <public-ip>
- Inside Interface: Mark the interface connected to the private network as ip nat inside.
- Outside Interface: Mark the interface connected to the public network as ip nat outside.
- Purpose: Static NAT ensures a fixed one-to-one mapping between a private and public IP address, typically used for servers or devices that need consistent public access.