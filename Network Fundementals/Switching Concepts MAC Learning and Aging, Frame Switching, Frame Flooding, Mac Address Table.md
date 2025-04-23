Related: [[Network Fundamentals]]

**MAC Learning and Aging**:  
Switches dynamically learn the MAC addresses of devices connected to their ports by examining the source MAC address of incoming Ethernet frames. When a frame is received, the switch records the source MAC address and the port it was received on in its MAC address table. This allows the switch to forward future frames destined for that MAC address directly to the correct port, improving efficiency.

- **Aging**: To prevent the MAC address table from becoming outdated or full, switches implement an aging timer. If no frames are received from a specific MAC address within the aging time (e.g., 300 seconds by default), the entry is removed from the table. This ensures that the table remains accurate and can accommodate new devices.

---

**Frame Switching**:  
Frame switching is the core function of a switch, where it forwards Ethernet frames between devices based on the destination MAC address. The process involves:

1. **Frame Reception**: The switch receives a frame on one of its ports.
2. **MAC Table Lookup**: The switch checks its MAC address table to find the port associated with the destination MAC address.
3. **Frame Forwarding**: If the destination MAC address is found in the table, the frame is forwarded to the corresponding port. If not, the frame is flooded (see Frame Flooding).  
    Frame switching ensures efficient communication within the network by directing traffic only to the intended recipient, reducing unnecessary traffic on other ports.

---

**Frame Flooding**:  
Frame flooding occurs when a switch receives a frame with a destination MAC address that is not in its MAC address table. Since the switch does not know which port to forward the frame to, it sends the frame out of all ports except the one it was received on. This ensures that the frame reaches its intended destination, even if the switch has not yet learned the destination MAC address.

- **Broadcast Frames**: Frames with a broadcast MAC address (e.g., `FF:FF:FF:FF:FF:FF`) are also flooded to all ports, as they are intended for all devices on the network.
- **Unknown Unicast Frames**: Frames with an unknown unicast destination are flooded until the switch learns the MAC address of the destination device.

---

**MAC Address Table**:  
The MAC address table (also known as the Content Addressable Memory or CAM table) is a database maintained by a switch that maps MAC addresses to specific switch ports. It is used to determine where to forward frames within the network.

- **Structure**: Each entry in the table includes the MAC address, the associated port, and an aging timer.
- **Learning**: The table is populated dynamically as the switch learns MAC addresses from incoming frames.
- **Efficiency**: By using the MAC address table, the switch can forward frames directly to the correct port, reducing unnecessary traffic and improving network performance.
- **Capacity**: The size of the MAC address table is limited, and exceeding its capacity can lead to issues like frame flooding.

In summary, these switching concepts work together to enable efficient, dynamic, and reliable communication within a network. The MAC address table and learning process ensure that traffic is directed appropriately, while frame flooding handles unknown destinations, and aging keeps the table up-to-date.