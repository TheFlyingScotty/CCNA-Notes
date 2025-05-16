Related: [[Rapid-PVST+]],[[Network Access]]

### Explanation of STP (Spanning Tree Protocol) Operation and Decision-Making:

**Spanning Tree Protocol (STP)** is a Layer 2 protocol used to prevent loops in a network with redundant paths. It ensures a loop-free topology by selectively blocking certain paths while keeping others active.

---

### How STP Operates:
1. **Bridge ID (BID):**
   - Each switch in the network has a unique **Bridge ID**, which is a combination of:
     - **Priority** (default is 32768, configurable).
     - **MAC Address** of the switch.
   - The switch with the lowest Bridge ID is elected as the **Root Bridge**.

2. **Root Bridge Election:**
   - All switches exchange **Bridge Protocol Data Units (BPDUs)** to determine the Root Bridge.
   - The switch with the lowest Bridge ID becomes the Root Bridge.

3. **Path Cost Calculation:**
   - STP assigns a **cost** to each link based on its bandwidth:
     - 10 Mbps: Cost = 100
     - 100 Mbps: Cost = 19
     - 1 Gbps: Cost = 4
     - 10 Gbps: Cost = 2
   - Each switch calculates the total cost to reach the Root Bridge. The path with the lowest cost is preferred.

4. **Port Roles:**
   - STP assigns roles to ports based on their function in the topology:
     - **Root Port (RP):** The port with the lowest cost to the Root Bridge.
     - **Designated Port (DP):** The port on each segment that provides the best path to the Root Bridge.
     - **Blocked Port:** Ports that are not part of the active topology to prevent loops.

5. **Port States:**
   - Ports transition through the following states:
     - **Blocking:** No data is forwarded; only BPDUs are received.
     - **Listening:** Listens for BPDUs to determine the topology.
     - **Learning:** Learns MAC addresses but does not forward data.
     - **Forwarding:** Forwards data and participates in the active topology.

6. **Topology Changes:**
   - If a link fails or a new switch is added, STP recalculates the topology by exchanging BPDUs.

---

### Cisco's Recommended Advice for Root Switch Selection:
Cisco recommends **manually configuring the Root Bridge** to ensure predictable network behavior. By default, the switch with the lowest Bridge ID (priority + MAC address) becomes the Root Bridge, which may not align with your network design.

#### Best Practices:
1. **Set Priority on Core or Distribution Switches:**
   - Use the `spanning-tree vlan <vlan-id> root primary` command to configure a switch as the Root Bridge for specific VLANs.
   - This sets the priority to a lower value (e.g., 24576) to ensure the switch is elected as the Root Bridge.

2. **Set a Secondary Root Bridge:**
   - Use the `spanning-tree vlan <vlan-id> root secondary` command to configure a backup Root Bridge with a slightly higher priority (e.g., 28672).

3. **Avoid Default Behavior:**
   - Do not rely on the default priority (32768), as it may result in an unintended switch becoming the Root Bridge.

4. **Consistency Across VLANs:**
   - In networks with multiple VLANs, ensure the same switch is the Root Bridge for all VLANs (or use Per-VLAN Spanning Tree [PVST] to designate different Root Bridges for different VLANs).

5. **Monitor and Verify:**
   - Use the `show spanning-tree` command to verify the Root Bridge and port roles in the topology.

---

### Example Configuration:
To configure a switch as the Root Bridge for VLAN 10:
```bash
Switch(config)# spanning-tree vlan 10 root primary
```

To configure a secondary Root Bridge for VLAN 10:
```bash
Switch(config)# spanning-tree vlan 10 root secondary
```

---

### Summary:
- STP prevents loops by electing a Root Bridge and blocking redundant paths.
- Cisco recommends manually configuring the Root Bridge on a core or distribution switch to ensure stability and predictability.
- Use the `spanning-tree` commands to set priorities and verify the topology.