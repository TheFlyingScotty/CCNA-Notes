Related:[[IP Services]]

Definition:
Network Address Translation (NAT) is a process used in networking to modify the IP address information in the headers of packets as they pass through a router or firewall. NAT allows multiple devices on a private network to share a single public IP address when accessing the internet.

Explanation:
NAT operates at the network layer (Layer 3) of the [[OSI model]]. It is commonly used to conserve public IP addresses and to provide a layer of security by hiding the internal IP addresses of devices on a private network. NAT translates private IP addresses (e.g., 192.168.x.x) into a public IP address when packets are sent to the internet and translates them back to the private IP address when responses are received.

Types of NAT:
1. [[Static NAT]]:
   - Maps a single private IP address to a single public IP address.
   - Use Case: Used when a specific internal device (e.g., a server) needs to be accessible from the internet using a fixed public IP address.

1. [[Dynamic NAT]]:
   - Maps a pool of private IP addresses to a pool of public IP addresses.
   - Use Case: Used when multiple internal devices need internet access, but there are fewer public IP addresses available than private devices.

1. [[Port Address Translation (PAT) (also called NAT Overload)]]
   - Maps multiple private IP addresses to a single public IP address by using different port numbers.
   - Use Case: The most common type of NAT, used in home and small business networks to allow many devices to share a single public IP address.

Use Cases:
1. **IP Address Conservation**:
   - NAT allows multiple devices to share a single public IP address, reducing the need for a large number of public IPs.

2. **Security**:
   - NAT hides the internal IP addresses of devices, making it harder for external attackers to directly target internal devices.

3. **Internet Access for Private Networks**:
   - NAT enables devices with private IP addresses (e.g., 192.168.x.x or 10.x.x.x) to access the internet by translating their private IPs to a public IP.

Example:
Consider a home network with the following setup:
- Private IPs: 192.168.1.2, 192.168.1.3, 192.168.1.4
- Public IP: 203.0.113.1

When a device (e.g., 192.168.1.2) sends a request to a website, NAT translates the private IP (192.168.1.2) to the public IP (203.0.113.1). When the response is received, NAT translates the public IP back to the private IP, ensuring the packet reaches the correct device.

Summary:
- **NAT**: Modifies IP addresses in packets to enable communication between private networks and the internet.
- **Types**: [[Static NAT]], [[Dynamic NAT]], and [[Port Address Translation (PAT) (also called NAT Overload)]].
- **Use Cases**: Conserves public IPs, enhances security, and enables internet access for private networks.