Related: [[NAT]]
Definition:
Dynamic Network Address Translation (Dynamic NAT) is a type of NAT where a pool of public IP addresses is used to dynamically map private IP addresses. Unlike Static NAT, the mapping is not fixed and changes as needed, depending on the availability of public IP addresses in the pool.

Explanation:
Dynamic NAT allows multiple devices on a private network to access the internet by temporarily assigning them a public IP address from a predefined pool. When a private device initiates a connection, the router assigns it an available public IP address from the pool. Once the session ends, the public IP address is returned to the pool for reuse by other devices.

Key Characteristics:
1. **Dynamic Mapping**:
   - Private IP addresses are dynamically mapped to public IP addresses from a pool.
   - The mapping is temporary and only lasts for the duration of the session.

2. **Limited Public IP Pool**:
   - The number of devices that can access the internet simultaneously is limited by the size of the public IP address pool.

3. **Outbound Communication Only**:
   - Dynamic NAT is typically used for outbound communication. Devices on the private network can initiate connections to the internet, but external devices cannot initiate connections to private devices.

Use Cases:
1. **Conserving Public IP Addresses**:
   - Dynamic NAT is used when there are fewer public IP addresses available than private devices. It allows efficient use of a limited number of public IPs.

2. **Temporary Internet Access**:
   - Suitable for networks where private devices only need temporary internet access, such as in offices or schools.

3. **Non-Persistent Connections**:
   - Used in scenarios where devices do not require a consistent public IP address, such as general web browsing or email access.

Example:
Consider a network with the following setup:
- Private IPs: 192.168.1.10, 192.168.1.11, 192.168.1.12
- Public IP Pool: 203.0.113.5, 203.0.113.6, 203.0.113.7

Dynamic NAT Configuration:
- The router is configured with a pool of public IPs (`203.0.113.5` to `203.0.113.7`).
- When `192.168.1.10` initiates a connection, it is temporarily assigned `203.0.113.5`.
- When `192.168.1.11` initiates a connection, it is assigned `203.0.113.6`.
- If all public IPs in the pool are in use, additional private devices must wait until a public IP becomes available.

Summary:
- **Dynamic NAT**: Dynamically maps private IPs to public IPs from a pool.
- **Key Features**: Temporary mapping, limited by the size of the public IP pool, and typically used for outbound communication.
- **Use Cases**: Conserving public IPs, providing temporary internet access, and supporting non-persistent connections.