Related: [[NAT]], [[Implementing PAT]]
Definition:
Port Network Address Translation (Port NAT), also called Port Address Translation (PAT), is a type of NAT that allows multiple devices on a private network to share a single public IP address by using different port numbers. PAT is also referred to as NAT Overload.

Explanation:
PAT works by mapping multiple private IP addresses and their source ports to a single public IP address with unique port numbers. When a device on the private network sends a packet to the internet, the router replaces the private IP address and port number with the public IP address and a unique port number. The router keeps track of these mappings in a NAT table to ensure that return traffic is sent to the correct private device.

Key Characteristics:
1. **Port Mapping**:
   - Each private device is assigned a unique port number on the public IP address for its session.
   - This allows multiple devices to share the same public IP address simultaneously.

2. **Efficient Use of Public IPs**:
   - PAT allows thousands of private devices to access the internet using a single public IP address, conserving public IP resources.

3. **Outbound Communication**:
   - PAT is primarily used for outbound communication. Devices on the private network can initiate connections to the internet, but external devices cannot directly initiate connections to private devices.

Use Cases:
1. **Home and Small Business Networks**:
   - PAT is commonly used in home and small business networks where multiple devices (e.g., computers, phones, printers) need internet access but only one public IP address is available.

2. **Public IP Address Conservation**:
   - PAT is ideal for networks with a large number of private devices but limited public IP addresses, as it allows all devices to share a single public IP.

3. **Dynamic and Temporary Connections**:
   - Suitable for scenarios where private devices only need temporary internet access, such as web browsing, email, or streaming.

Example:
Consider a network with the following setup:
- Private IPs: 192.168.1.10, 192.168.1.11, 192.168.1.12
- Public IP: 203.0.113.5

PAT Configuration:
- The router is configured to use the public IP `203.0.113.5` for NAT.
- When `192.168.1.10` initiates a connection, it is mapped to `203.0.113.5:1025`.
- When `192.168.1.11` initiates a connection, it is mapped to `203.0.113.5:1026`.
- When `192.168.1.12` initiates a connection, it is mapped to `203.0.113.5:1027`.
- The router keeps track of these mappings in a NAT table to ensure return traffic is sent to the correct private device.

Summary:
- **Port NAT (PAT)**: Maps multiple private IPs to a single public IP using unique port numbers.
- **Key Features**: Efficient use of public IPs, port mapping for session tracking, and primarily used for outbound communication.
- **Use Cases**: Home and small business networks, public IP conservation, and dynamic internet access for multiple devices.