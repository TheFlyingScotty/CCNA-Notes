
Related: HSRP, [[OSI model]]
**Definition**: A MAC (Media Access Control) address is a unique identifier assigned to a network interface controller (NIC) for use as a network address in communications within a network segment. MAC addresses are used in the data link layer of the [[OSI model]] and are essential for network communication.

### Explanation

1. **Format**:
    
    - A MAC address is typically represented as a 48-bit (6-byte) hexadecimal number.
    - It is usually written in one of the following formats:
        - `00:1A:2B:3C:4D:5E`
        - `00-1A-2B-3C-4D-5E`
        - `001A.2B3C.4D5E`
2. **Structure**:
    
    - The first 24 bits (3 bytes) represent the Organizationally Unique Identifier (OUI), which is assigned by the IEEE to the manufacturer.
    - The last 24 bits (3 bytes) represent the Network Interface Controller (NIC) specific identifier, which is assigned by the manufacturer.
3. **Purpose**:
    
    - MAC addresses are used to uniquely identify devices on a local network.
    - They are essential for the functioning of Ethernet and Wi-Fi networks, enabling devices to communicate with each other.
4. **Usage**:
    
    - **Data Link Layer**: MAC addresses operate at the data link layer (Layer 2) of the OSI model.
    - **Frame Forwarding**: Switches use MAC addresses to forward frames to the correct destination within a local network.
    - **Address Resolution Protocol (ARP)**: ARP is used to map IP addresses to MAC addresses, allowing devices to locate each other on the network.

### Example

Here is an example of a MAC address and its components:

- **MAC Address**: `00:1A:2B:3C:4D:5E`
    - **OUI (Manufacturer)**: `00:1A:2B` (assigned to the manufacturer)
    - **NIC Specific**: `3C:4D:5E` (assigned by the manufacturer to the specific device)

### Summary

- **MAC Address**: A unique identifier for network interfaces, used for communication within a local network.
- **Format**: 48-bit hexadecimal number, typically written as `00:1A:2B:3C:4D:5E`.
- **Structure**: Composed of an OUI (first 24 bits) and a NIC specific identifier (last 24 bits).
- **Purpose**: Enables devices to communicate on Ethernet and Wi-Fi networks, operating at the data link layer of the OSI model.