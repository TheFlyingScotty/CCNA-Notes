Related: [[Network Fundamentals]]

IPv6 Unicast addresses are used to identify a single interface on a device, and packets sent to a unicast address are delivered to that specific interface. There are three main types of IPv6 unicast addresses:

1. **Global Unicast**:
    
    - These are globally routable addresses, similar to public IPv4 addresses.
    - They are used for communication over the internet.
    - Typically assigned by an ISP and unique across the entire internet.
    - Prefix: Usually starts with `2000::/3`.
2. **Unique Local**:
    
    - These are private addresses used within an organization, similar to IPv4 private addresses (e.g., 192.168.x.x).
    - They are not routable on the internet but can be routed within a private network.
    - Useful for internal communication and isolated networks.
    - Prefix: Starts with `FC00::/7`.
3. **Link-Local**:
    
    - These addresses are automatically assigned to every IPv6-enabled interface.
    - They are used for communication between nodes on the same link (e.g., within the same subnet).
    - Required for IPv6 operations like neighbor discovery and routing protocols.
    - Prefix: Starts with `FE80::/10`.

In summary, global unicast addresses are for internet communication, unique local addresses are for private internal use, and link-local addresses are for communication within the same link or subnet.