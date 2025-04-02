Related:[[IP Services]],[[DHCP Relay]],[[DHCP Commands]]
Definition:
Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automatically assign IP addresses and other network configuration parameters (such as subnet mask, default gateway, and DNS servers) to devices on a network.

Explanation:
DHCP eliminates the need for manual IP address configuration by dynamically assigning IP addresses to devices when they join the network. A DHCP server maintains a pool of available IP addresses and leases them to devices for a specific period. When a device's lease expires, it can renew the lease or request a new IP address.

Key Features:
1. **Dynamic IP Assignment**:
   - Automatically assigns IP addresses to devices, reducing administrative overhead.
2. **Lease Duration**:
   - IP addresses are assigned for a limited time (lease), ensuring efficient use of the address pool.
3. **Configuration Parameters**:
   - Provides additional settings like subnet mask, default gateway, and DNS server addresses.

Use Cases:
1. **Simplified Network Management**:
   - Ideal for networks with many devices, such as offices, schools, and public Wi-Fi networks.
2. **Dynamic Environments**:
   - Useful in environments where devices frequently join and leave the network, such as guest networks.

DHCP Process:
1. **Discovery**:
   - The client broadcasts a DHCPDISCOVER message to find a DHCP server.
2. **Offer**:
   - The DHCP server responds with a DHCPOFFER message, offering an IP address and configuration details.
3. **Request**:
   - The client sends a DHCPREQUEST message to accept the offered IP address.
4. **Acknowledgment**:
   - The server sends a DHCPACK message to confirm the lease and finalize the configuration.

Summary:
DHCP simplifies IP address management by dynamically assigning and managing IP addresses and network settings, making it essential for modern networks.