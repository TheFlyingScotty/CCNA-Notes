Related: [[DHCP]]

1. configure terminal
   - Enters global configuration mode from privileged EXEC mode.
   - This mode allows you to configure global settings for the router, such as interfaces, routing protocols, and services.

2. enable
   - Enters privileged EXEC mode from user EXEC mode.
   - Privileged EXEC mode provides access to all router commands, including configuration, debugging, and monitoring commands.

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
   - This is useful when the router is acting as a DHCP client and needs to acquire an IP address automatically.

9. ipconfig /all
   - Used in NetSim to display the IP addresses and Media Access Control (MAC) address on a workstation.
   - This command provides detailed information about the workstation's network configuration, including IP address, subnet mask, default gateway, and DNS servers.

10. ipconfig /ip dhcp
    - Used in NetSim to configure the workstation to obtain IP addressing information from a DHCP server.
    - This command enables the workstation to request an IP address, subnet mask, and other configuration details from the DHCP server.

11. ip dhcp client lease {days [hours] [minutes] | infinite}
    - Requests a custom lease duration for DHCP clients.
    - For example, you can specify how long the DHCP client should retain its assigned IP address before requesting a renewal.

12. ip dhcp excluded-address ip-address [last-ip-address]
    - Configures a range of excluded addresses that the DHCP server will not assign to clients.
    - Example: `ip dhcp excluded-address 192.168.1.1 192.168.1.10` excludes the range 192.168.1.1 to 192.168.1.10 from being assigned to DHCP clients.

13. ip dhcp pool pool-name
    - Creates a DHCP address pool with the specified name.
    - Example: `ip dhcp pool LAN_POOL` creates a pool named LAN_POOL for assigning IP addresses to clients.

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

17. show dhcp lease
    - Displays the IP address lease duration for DHCP clients.
    - This command shows the remaining time for each DHCP lease.

18. show dhcp server
    - Displays IP configuration information contained in DHCPOFFER packets.
    - This includes details about the IP address, subnet mask, and other parameters offered by the DHCP server.

19. show ip dhcp binding
    - Displays active DHCP-assigned IP addresses.
    - This command shows the IP addresses currently leased to clients, along with their MAC addresses and lease expiration times.

20. show ip dhcp pool
    - Displays a basic summary of a configured DHCP pool.
    - This includes details such as the pool name, total addresses, and the number of addresses currently in use.

21. show ip dhcp server statistics
    - Displays general operating statistics for the DHCP server process.
    - This includes information such as the number of DHCP requests, offers, and acknowledgments processed by the server.

22. show ip interface brief
    - Displays a brief summary of interface status and configuration.
    - This includes the interface name, IP address, status (up/down), and protocol state.

23. show ip route
    - Displays the IP routing table.
    - This command shows the routes known to the router, including directly connected networks, static routes, and routes learned through dynamic routing protocols.

24. show running-config
    - Displays the active configuration file currently running on the router.
    - This includes all configured settings, such as interfaces, routing protocols, and DHCP configurations.