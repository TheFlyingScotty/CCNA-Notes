Related: [[Network Access]], [[CDP]]

LLDP (Link Layer Discovery Protocol) is a vendor-neutral Layer 2 protocol defined by IEEE 802.1AB. It is used by network devices to advertise their identity, capabilities, and connectivity information to directly connected devices on the same network. LLDP operates over Ethernet and is similar to Cisco's proprietary [[CDP]] (Cisco Discovery Protocol), but it is designed to work across devices from different vendors.

### Detailed Explanation:

1. **How LLDP Works**:
    
    - LLDP operates at the Data Link Layer (Layer 2) of the OSI model.
    - Devices periodically send LLDP advertisements (LLDP Data Units or LLDPDUs) containing information about themselves.
    - These advertisements are sent to a reserved multicast address and are not forwarded by switches, ensuring they remain within the local link.
    - LLDP information is stored in a device's LLDP neighbor table, which can be queried for details about directly connected devices.
2. **Information Advertised by LLDP**:
    
    - Device identity (e.g., hostname, system name).
    - Port information (e.g., port ID, description).
    - Capabilities (e.g., switch, router, access point).
    - VLAN information.
    - Power over Ethernet (PoE) requirements (for devices like IP phones or access points).
    - Management IP address.
3. **Configuration**:
    
    - LLDP is typically enabled globally on network devices.
    - It can be configured to operate on specific interfaces or disabled where not needed.
4. **Standards**:
    
    - LLDP is standardized under IEEE 802.1AB, ensuring interoperability between devices from different vendors.

---

### Use Cases:

1. **Network Topology Discovery**:
    
    - LLDP helps administrators discover the physical topology of the network by identifying directly connected devices and their interfaces.
2. **Troubleshooting**:
    
    - LLDP provides detailed information about connected devices, such as port IDs and system names, which can be used to diagnose connectivity issues.
3. **Power over Ethernet (PoE) Management**:
    
    - LLDP-MED (Media Endpoint Discovery), an extension of LLDP, is used to negotiate PoE requirements for devices like IP phones and access points.
4. **Device Configuration**:
    
    - LLDP-MED can be used to automatically configure VoIP devices by providing VLAN and QoS settings.
5. **Interoperability**:
    
    - LLDP enables communication and discovery between devices from different vendors, making it ideal for heterogeneous network environments.

---

### Example:

- **Scenario**: An administrator wants to identify which switch port an IP phone is connected to.
- **Solution**: Using LLDP, the administrator can query the switch to see the LLDP neighbor table, which will display the IP phone's details (e.g., hostname, port, and PoE requirements).

---

### Summary:

LLDP is a vendor-neutral protocol that simplifies network management by enabling devices to advertise and discover information about directly connected neighbors. It is widely used for topology discovery, troubleshooting, PoE management, and ensuring interoperability in multi-vendor environments.