Related: [[IP Services]], [[Configuring an NTP Client]],[[Configuring an NTP Server]]
Definition:
Network Time Protocol (NTP) is a protocol used to synchronize the clocks of devices on a network to a common time source. NTP ensures that all devices in a network have accurate and consistent time, which is critical for logging, security, and time-sensitive applications.

Explanation:
NTP operates at Layer 7 (Application Layer) of the [[OSI model]] and uses UDP port 123 for communication. It synchronizes time by exchanging time information between devices, such as servers, routers, switches, and computers. NTP can synchronize time to within milliseconds of the reference clock.

Key Features:
1. **Hierarchy of Time Sources**:
   - NTP uses a hierarchical system of time sources, organized into levels called "stratum."
   - Stratum 0: High-precision time sources (e.g., atomic clocks, GPS clocks).
   - Stratum 1: Devices directly connected to Stratum 0 sources (e.g., NTP servers).
   - Stratum 2: Devices synchronized to Stratum 1 servers, and so on.

2. **Clock Synchronization**:
   - NTP adjusts the local clock gradually to avoid abrupt changes, ensuring smooth synchronization.

3. **Redundancy**:
   - NTP can use multiple time sources for redundancy and accuracy. It selects the best source based on factors like delay and jitter.

4. **Authentication**:
   - NTP supports authentication to ensure that time updates come from trusted sources.

Use Cases:
1. **Log Accuracy**:
   - Ensures accurate timestamps in system logs, which is critical for troubleshooting and auditing.

2. **Security**:
   - Synchronizes time for security protocols like Kerberos, which rely on accurate time for authentication.

3. **Time-Sensitive Applications**:
   - Used in applications like financial transactions, video conferencing, and industrial automation, where precise timing is essential.

4. **Network Coordination**:
   - Ensures consistent time across devices in a network for coordinated operations.

Example Configuration:
Suppose you want to configure a Cisco router to synchronize its clock with an NTP server at IP address 192.168.1.100.

Commands:
1. Enter global configuration mode:
   configure terminal

2. Configure the NTP server:
   ntp server 192.168.1.100
   Explanation:
   This command tells the router to synchronize its clock with the NTP server at 192.168.1.100.

3. (Optional) Enable NTP authentication:
   ntp authenticate
   ntp authentication-key 1 md5 mypassword
   ntp trusted-key 1
   ntp server 192.168.1.100 key 1
   Explanation:
   These commands enable NTP authentication, configure a key (ID 1) with the password "mypassword," and associate the key with the NTP server.

4. Verify the NTP configuration:
   show ntp status
   Explanation:
   This command displays the NTP synchronization status, including whether the device is synchronized and the stratum level of the time source.

5. Save the configuration:
   write memory
   Explanation:
   This command saves the configuration to ensure it persists after a reboot.

Summary:
- NTP synchronizes the clocks of devices on a network to a common time source.
- It uses a hierarchical system of time sources (stratum levels) for accuracy and redundancy.
- Use Cases: Log accuracy, security, time-sensitive applications, and network coordination.
- Configuration involves specifying an NTP server, optionally enabling authentication, and verifying synchronization.