
Related: [[DHCP Relay]]
1. configure terminal
   - Enters global configuration mode from privileged EXEC mode.
   - This mode allows you to configure global settings for the router, such as interfaces, routing protocols, and services.

2. enable
   - Enters privileged EXEC mode from user EXEC mode.
   - Privileged EXEC mode provides access to all router commands, including configuration and debugging commands.

3. end
   - Exits configuration mode and returns to privileged EXEC mode.
   - This command is used to quickly exit any configuration sub-mode and return to the main privileged EXEC prompt.

4. exit
   - Exits one level in the menu structure.
   - For example, if you are in interface configuration mode, this command will return you to global configuration mode.

5. default-router address
   - Specifies the IP address of a default gateway for DHCP clients.
   - This is used to configure the default gateway that DHCP clients will use to send traffic outside their local subnet.

6. domain-name domain
   - Specifies the domain name for a DHCP client.
   - This is used to assign a domain name (e.g., example.com) to DHCP clients, which can be useful for DNS resolution.

7. interface type number
   - Changes from global configuration mode to interface configuration mode.
   - For example, `interface GigabitEthernet0/0` allows you to configure settings specific to the GigabitEthernet0/0 interface.

8. ip address dhcp
   - Configures a router interface to obtain its IP address dynamically from a DHCP server.
   - This is useful when the router is acting as a DHCP client.

9. ipconfig /ip dhcp
   - Used in NetSim to configure a workstation to obtain IP addressing information from a DHCP server.
   - This command enables the workstation to request an IP address, subnet mask, and other configuration details from the DHCP server.

10. ip dhcp client lease {days [hours] [minutes] | infinite}
    - Requests a custom lease duration for DHCP clients.
    - For example, you can specify how long the DHCP client should retain its assigned IP address before requesting a renewal.

11. [no] ip dhcp excluded-address ip-address [last-ip-address]
    - Configures a range of excluded addresses that the DHCP server will not assign to clients.
    - The `no` form removes the specified address or range from the exclusion list.
    - Example: `ip dhcp excluded-address 192.168.1.1 192.168.1.10` excludes the range 192.168.1.1 to 192.168.1.10.

12. [no] ip dhcp pool pool-name
    - Creates a DHCP address pool with the specified name.
    - The `no` form removes the specified DHCP pool.
    - Example: `ip dhcp pool LAN_POOL` creates a pool named LAN_POOL.

13. ip helper-address ip-address
    - Configures a DHCP relay agent for a particular interface.
    - This command forwards DHCP requests from clients in one subnet to a DHCP server in another subnet.
    - Example: `ip helper-address 192.168.1.100` forwards DHCP requests to the server at 192.168.1.100.

14. lease {days [hours [minutes]] | infinite}
    - Configures a custom lease duration for DHCP assignments.
    - Example: `lease 7 12` sets a lease duration of 7 days and 12 hours.

15. network ip-address subnet-mask
    - Enables a DHCP server for a particular network segment.
    - This command specifies the network and subnet mask for which the DHCP server will assign IP addresses.
    - Example: `network 192.168.1.0 255.255.255.0` enables DHCP for the 192.168.1.0/24 network.

16. [no] service dhcp
    - Configures the router to respond to DHCP requests.
    - The `no` form disables the DHCP service and prevents the router from acting as a DHCP server or relay agent.

17. show ip dhcp binding
    - Displays active DHCP-assigned IP addresses.
    - This command shows the IP addresses currently leased to clients, along with their MAC addresses and lease expiration times.

18. show ip dhcp pool
    - Displays a basic summary of a configured DHCP pool.
    - This includes details such as the pool name, total addresses, and the number of addresses currently in use.

19. show ip dhcp server statistics
    - Displays general operating statistics for the DHCP server process.
    - This includes information such as the number of DHCP requests, offers, and acknowledgments processed by the server.

20. show running-config
    - Displays the active configuration file currently running on the router.
    - This includes all configured settings, such as interfaces, routing protocols, and DHCP configurations.