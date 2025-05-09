
Related: [[IP Connectivity]]

### **Definition of SDM (Switch Database Management)**:

SDM (Switch Database Management) is a feature on Cisco switches that allows administrators to optimize the allocation of hardware resources (such as memory and forwarding tables) for specific network roles or use cases. It determines how the switch's hardware resources are divided between Layer 2 switching, Layer 3 routing, IPv4, IPv6, multicast, and other features.

---

### **Explanation**:

1. **Purpose**:
    
    - Cisco switches have limited hardware resources, such as TCAM (Ternary Content Addressable Memory), which is used for storing MAC addresses, routing tables, ACLs, and QoS policies.
    - The SDM templates allow you to customize how these resources are allocated based on the network's requirements.
2. **Templates**:
    
    - SDM templates are pre-defined configurations that optimize the switch for specific tasks. Common templates include:
        - **Default**: Balanced allocation for Layer 2 switching and basic Layer 3 routing.
        - **VLAN**: Optimized for Layer 2 VLAN switching, with minimal Layer 3 routing support.
        - **Routing**: Allocates more resources for Layer 3 routing (IPv4 and IPv6).
        - **Access**: Optimized for access-layer switches with a focus on Layer 2 features.
        - **Dual IPv4 and IPv6 Routing**: Allocates resources for both IPv4 and IPv6 routing.
3. **Reload Requirement**:
    
    - Changing the SDM template requires a switch reload for the new resource allocation to take effect.
4. **Verification**:
    
    - Use the `show sdm prefer` command to verify the active SDM template.

---

### **Use Cases**:

1. **Layer 2 Switching (VLAN Template)**:
    
    - Use the **VLAN** template for switches primarily used for Layer 2 VLAN switching.
    - Example: A switch in an access layer with many VLANs and minimal routing requirements.
2. **Inter-VLAN Routing (Routing or Dual IPv4 and IPv6 Routing Template)**:
    
    - Use the **Routing** or **Dual IPv4 and IPv6 Routing** template for switches that need to perform inter-VLAN routing or act as a Layer 3 device.
    - Example: A multilayer switch in a distribution layer that routes traffic between VLANs.
3. **IPv6 Support (Dual IPv4 and IPv6 Routing Template)**:
    
    - Use the **Dual IPv4 and IPv6 Routing** template for environments that require both IPv4 and IPv6 routing.
    - Example: A network transitioning to IPv6 while still supporting IPv4.
4. **Default Template**:
    
    - Use the **Default** template for general-purpose switches that require a balance between Layer 2 and Layer 3 features.
    - Example: A small network where the switch handles both VLANs and basic routing.
5. **High Multicast Traffic**:
    
    - Use a template that allocates more resources for multicast traffic if the network heavily relies on multicast applications (e.g., video streaming).

---

### **Summary**:

- **SDM (Switch Database Management)** is a feature that optimizes hardware resource allocation on Cisco switches.
- It allows customization for specific roles, such as Layer 2 switching, Layer 3 routing, or dual IPv4/IPv6 support.
- **Use Cases**:
    - VLAN template for Layer 2 switching.
    - Routing template for inter-VLAN routing.
    - Dual IPv4 and IPv6 template for networks requiring both IPv4 and IPv6 routing.
- Changing the SDM template requires a reload and can be verified using `show sdm prefer`.