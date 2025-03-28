
Related: [[NAT]], [[Implementing Static NAT]]


Definition:
Static Network Address Translation (Static NAT) is a type of NAT where a single private IP address is permanently mapped to a single public IP address. This mapping is one-to-one and does not change, allowing devices on a private network to be consistently accessible from the public network.

Explanation:
Static NAT is used to provide a fixed public IP address for a specific internal device, such as a server, so it can be accessed from the internet. Unlike Dynamic NAT or PAT, the mapping in Static NAT is manually configured and remains constant. This ensures that the internal device always uses the same public IP address for communication.

Key Characteristics:
1. **One-to-One Mapping**:
   - Each private IP address is mapped to a single public IP address.
   - The mapping is static and does not change.

2. **Bidirectional Communication**:
   - Static NAT allows both inbound and outbound communication.
   - External devices can initiate communication with the internal device using the public IP address.

3. **Manual Configuration**:
   - The NAT mappings must be manually configured by the network administrator.

Use Cases:
1. **Hosting Services**:
   - Static NAT is commonly used for servers that need to be accessible from the internet, such as web servers, email servers, or FTP servers.

2. **Remote Access**:
   - Used to provide remote access to specific devices on a private network, such as security cameras or management systems.

3. **Consistent Public IP**:
   - Ensures that a specific internal device always uses the same public IP address, which is useful for applications that require a fixed IP (e.g., VPNs or licensing servers).

Example:
Consider a network with the following setup:
- Private IP: 192.168.1.10 (internal web server)
- Public IP: 203.0.113.5 (mapped to the web server)

Static NAT Configuration:
- The router is configured to map the private IP `192.168.1.10` to the public IP `203.0.113.5`.
- When an external user accesses `203.0.113.5`, the router translates the public IP to `192.168.1.10` and forwards the traffic to the web server.
- Similarly, when the web server sends traffic to the internet, the router translates `192.168.1.10` to `203.0.113.5`.

Summary:
- **Static NAT**: Provides a permanent one-to-one mapping between a private IP and a public IP.
- **Key Features**: Fixed mapping, bidirectional communication, and manual configuration.
- **Use Cases**: Hosting public-facing services, remote access, and applications requiring a consistent public IP.