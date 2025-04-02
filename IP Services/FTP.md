Related: [[IP Services]],[[FTP Commands]]

Definition:
File Transfer Protocol (FTP) is a standard network protocol used to transfer files between a client and a server over a network. FTP operates on TCP ports 20 and 21, providing reliable and secure file transfers with support for authentication and various file management operations.

Explanation:
FTP allows users to upload, download, delete, rename, and manage files on a remote server. It uses a client-server model, where the client initiates a connection to the server to perform file operations. FTP supports both anonymous access (no credentials required) and authenticated access (username and password).

Key Features:
1. **Reliable File Transfers**:
   - FTP uses TCP, ensuring reliable delivery of files with error checking and retransmission.
2. **Authentication**:
   - Supports user authentication with usernames and passwords for secure access.
3. **File Management**:
   - Allows users to perform operations like renaming, deleting, and listing files on the server.
4. **Active and Passive Modes**:
   - FTP can operate in active mode (server initiates data connection) or passive mode (client initiates data connection), depending on firewall configurations.

Differences Between FTP and TFTP:
1. **Protocol**:
   - FTP uses TCP (reliable, connection-oriented).
   - TFTP uses UDP (faster but less reliable).

2. **Authentication**:
   - FTP supports authentication with usernames and passwords.
   - TFTP does not support authentication, making it less secure.

3. **Features**:
   - FTP provides advanced file management features like renaming and deleting files.
   - TFTP is limited to basic file transfers.

4. **Use Cases**:
   - FTP is used for general-purpose file transfers, including large files and secure access.
   - TFTP is used for simple, lightweight file transfers in trusted environments, such as transferring configuration files or firmware.

5. **Ports**:
   - FTP uses TCP ports 20 (data) and 21 (control).
   - TFTP uses UDP port 69.

Summary:
FTP is a reliable and feature-rich protocol for transferring and managing files over a network, supporting authentication and advanced operations. Compared to TFTP, FTP is more secure and versatile but requires more resources and configuration.