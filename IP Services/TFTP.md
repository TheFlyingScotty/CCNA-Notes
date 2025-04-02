Related: [[IP Services]],[[TFTP Commands]]

Definition:
Trivial File Transfer Protocol (TFTP) is a simple, lightweight protocol used to transfer files between devices over a network. It operates on UDP port 69 and is commonly used for transferring configuration files, firmware, and boot files in network environments.

Explanation:
TFTP is a simplified version of the File Transfer Protocol (FTP) and does not include advanced features like authentication or encryption. It is designed for quick and easy file transfers in trusted and controlled environments, such as within a local network.

Key Features:
1. **Lightweight Protocol**:
   - TFTP is simple and requires minimal resources, making it ideal for embedded systems and devices with limited processing power.
2. **No Authentication**:
   - TFTP does not require user authentication, which simplifies its use but makes it less secure.
3. **Uses UDP**:
   - TFTP uses the connectionless UDP protocol, which makes it faster but less reliable than TCP-based protocols.
4. **Common Use Cases**:
   - Transferring router and switch configuration files.
   - Uploading or downloading firmware and operating system images.
   - Booting diskless workstations or devices.

Differences between TFTP and FTP:
- TFTP does not require authentication.
- TFTP supports only unidirectional transfer.
- TFTP relies on a single UDP port instead of two TCP ports.
- Cisco IOS devices can be configured to boot from a TFTP server.


Use Cases:
1. **Network Device Configuration**:
   - TFTP is used to back up or restore configuration files on routers, switches, and firewalls.
2. **Firmware Updates**:
   - Network devices use TFTP to download firmware or operating system updates.
3. **PXE Boot**:
   - TFTP is used in Preboot Execution Environment (PXE) to transfer boot files to diskless workstations.

Limitations:
1. **No Security**:
   - TFTP lacks encryption and authentication, making it unsuitable for transferring sensitive data over untrusted networks.
2. **Unreliable**:
   - Since it uses UDP, TFTP does not guarantee delivery of packets, which can lead to data loss in unreliable networks.

Summary:
TFTP is a simple protocol for transferring files over a network, commonly used for configuration backups, firmware updates, and booting devices. It is lightweight and fast but lacks security and reliability, making it best suited for trusted and controlled environments.