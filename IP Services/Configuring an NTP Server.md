Related: [[NTP]]
Definition:
An NTP server is a device that provides accurate time information to NTP clients on a network. The NTP server synchronizes its own clock with a higher-level time source (e.g., a Stratum 1 server, GPS clock, or atomic clock) and distributes this time to clients. It ensures that all devices in the network maintain consistent and accurate time.

Explanation:
An NTP server operates at a specific stratum level:
- Stratum 1: Directly connected to a high-precision time source, such as a GPS or atomic clock.
- Stratum 2: Synchronizes with a Stratum 1 server and provides time to clients.
- Stratum 3 and below: Synchronizes with higher-stratum servers and provides time to lower-stratum clients.

NTP servers are critical for maintaining accurate time across a network, which is essential for logging, security, and time-sensitive applications.

Use Cases:
1. **Centralized Time Source**:
   - Provides a single, consistent time source for all devices in a network.
2. **Accurate Logging**:
   - Ensures that logs across devices have synchronized timestamps for troubleshooting and auditing.
3. **Security Protocols**:
   - Supports time-sensitive security mechanisms like Kerberos and digital certificates.
4. **Time-Sensitive Applications**:
   - Used in applications like financial transactions, industrial automation, and video conferencing.

How to Configure an NTP Server:
Below are the steps and commands to configure a Cisco device as an NTP server.

1. Enter Global Configuration Mode:
   Command:
   configure terminal
   Explanation:
   This command puts the device into global configuration mode, allowing you to make configuration changes.

2. Enable NTP Server Functionality:
   Command:
   ntp master <stratum-level>
   Example:
   ntp master 3
   Explanation:
   This command configures the device as an NTP server with a specific stratum level (e.g., 3). The stratum level indicates the server's position in the NTP hierarchy. A lower stratum level indicates a more accurate time source.

3. (Optional) Synchronize with an External Time Source:
   Command:
   ntp server <external-ntp-server-ip>
   Example:
   ntp server 192.168.1.100
   Explanation:
   This command configures the NTP server to synchronize its clock with an external NTP server (e.g., a Stratum 1 or Stratum 2 server). This ensures the NTP server provides accurate time to its clients.

4. (Optional) Configure NTP Authentication:
   Command:
   ntp authenticate
   ntp authentication-key <key-id> md5 <password>
   ntp trusted-key <key-id>
   Example:
   ntp authenticate
   ntp authentication-key 1 md5 mypassword
   ntp trusted-key 1
   Explanation:
   These commands enable NTP authentication, configure a key (ID 1) with the password "mypassword," and ensure that only trusted clients can synchronize with the server.

5. Save the Configuration:
   Command:
   write memory
   Explanation:
   This command saves the configuration to ensure it persists after a reboot.

Complete Example Configuration:
Suppose you want to configure a Cisco router as an NTP server with a stratum level of 3 and synchronize it with an external NTP server at IP address 192.168.1.100.

Commands:
configure terminal
ntp master 3
ntp server 192.168.1.100
ntp authenticate
ntp authentication-key 1 md5 mypassword
ntp trusted-key 1
exit
write memory

Verification:
1. Use the command show ntp status to check if the server is synchronized with the external time source.
2. Use the command show ntp associations to view the details of the external NTP server and its synchronization status.

Summary:
- An NTP server provides accurate time to NTP clients on a network.
- Use Cases: Centralized time source, accurate logging, security protocols, and time-sensitive applications.
- Configuration involves enabling NTP server functionality, optionally synchronizing with an external time source, and verifying synchronization.