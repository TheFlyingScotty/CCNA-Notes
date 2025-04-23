Related: [[IPV6]],[[Network Fundamentals]]

Modified EUI-64 is a method used in IPv6 to automatically generate an interface identifier (the last 64 bits of an IPv6 address) from a device's MAC address. This ensures that each device has a unique IPv6 address without requiring manual configuration.

### How Modified EUI-64 Works:

1. **Start with the MAC Address**:
    
    - A MAC address is a 48-bit hardware address assigned to a network interface card (NIC).
2. **Split the MAC Address**:
    
    - The MAC address is divided into two 24-bit halves.
3. **Insert the "FFFE" Value**:
    
    - The value `FFFE` (16 bits) is inserted between the two halves of the MAC address, expanding it to 64 bits.
4. **Flip the 7th Bit (Universal/Local Bit)**:
    
    - The 7th bit of the first byte (the Universal/Local bit) is inverted:
        - If the bit is `0` (indicating a globally unique MAC address), it is changed to `1`.
        - If the bit is `1` (indicating a locally administered MAC address), it is changed to `0`.
5. **Resulting Interface Identifier**:
    
    - The modified 64-bit value becomes the interface identifier, which is appended to the network prefix to form the full IPv6 address.

### Example:

1. **Original MAC Address**: `00:1A:2B:3C:4D:5E`
2. **Split into Halves**: `00:1A:2B` and `3C:4D:5E`
3. **Insert FFFE**: `00:1A:2B:FF:FE:3C:4D:5E`
4. **Flip the 7th Bit**: `02:1A:2B:FF:FE:3C:4D:5E`
5. **Resulting Interface Identifier**: `021A:2BFF:FE3C:4D5E`

### Advantages of Modified EUI-64:

1. **Automatic Address Configuration**:
    - Simplifies IPv6 address assignment by generating unique interface identifiers automatically.
2. **Global Uniqueness**:
    - Ensures that each device has a unique IPv6 address when using globally unique MAC addresses.

### Disadvantages:

1. **Privacy Concerns**:
    - Since the interface identifier is derived from the MAC address, it can reveal the device's hardware information and allow tracking across networks.
    - To address this, IPv6 also supports **Privacy Extensions**, which generate random interface identifiers.

### Use Case:

Modified EUI-64 is commonly used in Stateless Address Auto-Configuration (SLAAC), where devices generate their own IPv6 addresses based on the network prefix provided by a router and their interface identifier.

In summary, Modified EUI-64 is a method for generating unique IPv6 interface identifiers from MAC addresses, simplifying address configuration while ensuring uniqueness. However, it may raise privacy concerns in certain scenarios.