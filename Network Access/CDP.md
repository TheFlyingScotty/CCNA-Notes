Related: [[LLDP]], [[Network Access]]

CDP (Cisco Discovery Protocol) is a proprietary Layer 2 protocol developed by Cisco Systems. It is used by Cisco devices to share information about themselves with directly connected Cisco devices. CDP operates on the Data Link Layer (Layer 2) of the OSI model and is enabled by default on most Cisco devices.

### Detailed Explanation:

1. **How CDP Works**:
    
    - CDP allows Cisco devices to advertise their identity, capabilities, and configuration details to directly connected Cisco devices.
    - Devices periodically send CDP advertisements (CDP packets) to a multicast address. These packets are not forwarded by switches, ensuring they remain within the local link.
    - CDP information is stored in a device's CDP neighbor table, which can be queried to view details about connected devices.
2. **Information Advertised by CDP**:
    
    - Device ID (e.g., hostname).
    - Port ID (e.g., the interface sending the CDP packet).
    - Capabilities (e.g., switch, router, IP phone).
    - Platform (e.g., device model or type).
    - IP address of the device.
    - VLAN information (for switches).
    - Power over Ethernet (PoE) requirements (for devices like IP phones).
    - Software version running on the device.
3. **Configuration**:
    
    - CDP is enabled globally and on all interfaces by default on Cisco devices.
    - It can be disabled globally or on specific interfaces if not needed.
4. **Standards**:
    
    - CDP is a Cisco proprietary protocol and works only between Cisco devices or devices that support CDP.

---

### Use Cases:

1. **Network Topology Discovery**:
    
    - CDP helps administrators discover the physical topology of a Cisco network by identifying directly connected devices and their interfaces.
2. **Troubleshooting**:
    
    - CDP provides detailed information about connected devices, such as port IDs and system names, which can be used to diagnose connectivity issues.
3. **Power over Ethernet (PoE) Management**:
    
    - CDP can advertise PoE requirements for devices like IP phones, ensuring proper power allocation.
4. **Device Configuration**:
    
    - CDP can be used to identify connected devices and their configurations, simplifying network setup and management.
5. **Interoperability**:
    
    - CDP helps ensure smooth communication between Cisco devices in a network.

---

### Example:

- **Scenario**: An administrator wants to identify which switch port a Cisco IP phone is connected to.
- **Solution**: Using the `show cdp neighbors` command, the administrator can view the CDP neighbor table, which will display the IP phone's details (e.g., hostname, port, and PoE requirements).

---

### Commands for CDP:

1. **Enable/Disable CDP**:
    
    - Globally: `cdp run` (enable), `no cdp run` (disable).
    - On an interface: `cdp enable` (enable), `no cdp enable` (disable).
2. **View CDP Neighbors**:
    
    - `show cdp neighbors`: Displays a summary of directly connected devices.
    - `show cdp neighbors detail`: Provides detailed information about connected devices.

---

### Summary:

CDP is a Cisco proprietary protocol that simplifies network management by enabling Cisco devices to share information about themselves with directly connected neighbors. It is widely used for topology discovery, troubleshooting, PoE management, and ensuring efficient communication in Cisco-only environments. However, in multi-vendor networks, LLDP (Link Layer Discovery Protocol) is preferred for interoperability.