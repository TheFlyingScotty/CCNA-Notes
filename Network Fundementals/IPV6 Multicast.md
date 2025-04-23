Related: [[Network Fundamentals]], [[IPV6]]

IPv6 Multicast is an addressing method used to send data to multiple devices (a group) simultaneously. It allows efficient one-to-many communication by delivering packets to all devices that are members of a multicast group.

### Key Characteristics of IPv6 Multicast:

1. **One-to-Many Communication**:
    
    - Packets sent to a multicast address are delivered to all devices that have joined the multicast group.
2. **Special Address Range**:
    
    - IPv6 multicast addresses start with the prefix `FF00::/8`.
    - Example: `FF02::1` is a multicast address for all nodes on the local link.
3. **Efficient Bandwidth Usage**:
    
    - Multicast reduces bandwidth usage by sending a single copy of the data, which is then distributed to multiple recipients by the network.
4. **Scoped Addresses**:
    
    - Multicast addresses include a scope field to define the range of the multicast group:
        - **FF01::/16**: Interface-local scope (single interface).
        - **FF02::/16**: Link-local scope (same link or subnet).
        - **FF05::/16**: Site-local scope (within an organization).
        - **FF08::/16**: Organization-local scope.
        - **FF0E::/16**: Global scope (across the internet).
5. **No Broadcast in IPv6**:
    
    - IPv6 does not use broadcast addresses; multicast replaces broadcast functionality.

### Use Cases:

1. **Routing Protocols**:
    - IPv6 multicast is used by routing protocols like OSPFv3 and EIGRP to communicate between routers.
2. **Video and Audio Streaming**:
    - Multicast is ideal for streaming media to multiple users simultaneously.
3. **Neighbor Discovery**:
    - IPv6 uses multicast for neighbor discovery (e.g., `FF02::1` for all nodes and `FF02::2` for all routers).

### Example:

If a video server sends data to the multicast address `FF05::1`, all devices in the site-local multicast group `FF05::1` will receive the data.

In summary, IPv6 Multicast enables efficient one-to-many communication, reducing bandwidth usage and improving performance for applications like streaming, routing, and network discovery.