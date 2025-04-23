Related: [[Network Access]]

Cisco Access Points (APs) can operate in various modes to support different network requirements and deployment scenarios. Each mode serves a specific purpose, allowing administrators to configure the APs based on the needs of the wireless network.

### **1. Local Mode**:

- **Description**: This is the default mode for Cisco APs in a controller-based deployment.
- **Functionality**:
    - The AP handles client traffic and forwards it to the Wireless LAN Controller (WLC) for processing.
    - Performs periodic off-channel scanning for interference, rogue devices, and channel utilization while primarily serving clients.
- **Use Case**: Standard deployments where the AP provides wireless connectivity to clients.

---

### **2. FlexConnect Mode (H-REAP)**:

- **Description**: Allows APs to operate with or without a connection to the WLC.
- **Functionality**:
    - In connected mode, the AP forwards traffic to the WLC.
    - In standalone mode (when the WLC is unreachable), the AP can locally switch traffic and authenticate clients using cached credentials.
- **Use Case**: Remote or branch offices where connectivity to the central WLC may be intermittent.

---

### **3. Monitor Mode**:

- **Description**: The AP does not serve clients but instead scans the wireless environment.
- **Functionality**:
    - Detects rogue APs and clients.
    - Monitors interference and channel utilization.
    - Provides data for wireless intrusion prevention systems (WIPS).
- **Use Case**: Security and performance monitoring in the wireless network.

---

### **4. Sniffer Mode**:

- **Description**: The AP captures wireless traffic and forwards it to a network analyzer like Wireshark.
- **Functionality**:
    - Operates as a packet sniffer, capturing 802.11 frames for analysis.
    - Useful for troubleshooting and diagnosing wireless issues.
- **Use Case**: Wireless packet analysis and troubleshooting.

---

### **5. Rogue Detector Mode**:

- **Description**: The AP detects rogue devices on the wired network.
- **Functionality**:
    - Monitors ARP packets to identify rogue APs connected to the wired network.
    - Does not serve wireless clients.
- **Use Case**: Identifying and mitigating rogue APs in the network.

---

### **6. Bridge Mode**:

- **Description**: The AP acts as a wireless bridge to connect two or more wired networks.
- **Functionality**:
    - Supports point-to-point or point-to-multipoint bridging.
    - Extends the wired network over a wireless link.
- **Use Case**: Connecting remote buildings or locations without physical cabling.

---

### **7. SE-Connect Mode (Spectrum Expert)**:

- **Description**: The AP operates as a spectrum analyzer.
- **Functionality**:
    - Provides detailed RF analysis, including interference sources and spectrum usage.
    - Requires Cisco Spectrum Expert software for visualization.
- **Use Case**: Advanced RF troubleshooting and interference detection.

---

### **8. Flex+Bridge Mode**:

- **Description**: Combines FlexConnect and Bridge modes.
- **Functionality**:
    - Allows the AP to act as a bridge while also providing local switching for client traffic.
- **Use Case**: Remote sites requiring both bridging and local client connectivity.

---

### **9. Mesh Mode**:

- **Description**: The AP operates as part of a wireless mesh network.
- **Functionality**:
    - Provides wireless backhaul connectivity between APs.
    - Extends the network to areas where wired connections are not feasible.
- **Use Case**: Outdoor or large-scale deployments requiring extended coverage.

---

### **10. Client Mode**:

- **Description**: The AP acts as a wireless client.
- **Functionality**:
    - Connects to another AP as a client, providing network access to wired devices connected to its Ethernet port.
- **Use Case**: Temporary network access for wired devices in areas without wired infrastructure.

---

### Summary:

Cisco AP modes provide flexibility for various deployment scenarios, including standard client connectivity (Local Mode), remote office support (FlexConnect), security monitoring (Monitor and Rogue Detector Modes), troubleshooting (Sniffer and SE-Connect Modes), and specialized use cases like bridging and mesh networking. Administrators can select the appropriate mode based on the specific requirements of their wireless network.