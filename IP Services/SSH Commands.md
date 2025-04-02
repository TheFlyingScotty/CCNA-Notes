Related: [[SSH]]

1. configure terminal
   - Enters global configuration mode from privileged EXEC mode.
   - This mode allows you to configure global settings for the device, such as interfaces, routing protocols, and security features.

2. end
   - Exits configuration mode and returns to privileged EXEC mode.
   - This command is used to quickly exit any configuration sub-mode and return to the main privileged EXEC prompt.

3. exit
   - Exits one level in the menu structure.
   - For example, if you are in line configuration mode, this command will return you to global configuration mode.

4. ip domain-name name
   - Defines a default domain name for the device.
   - This is required for generating SSH keys and completing unqualified hostnames during DNS lookups.
   - Example: `ip domain-name example.com`

5. ip ssh version [1 | 2]
   - Specifies the version of SSH to be used on the device.
   - Version 2 is more secure and recommended for modern networks.
   - Example: `ip ssh version 2`

6. line vty 0 15
   - Enters configuration mode for the specified VTY (Virtual Terminal) lines.
   - VTY lines are used for remote access to the device via protocols like SSH and Telnet.
   - Example: `line vty 0 15` configures all 16 VTY lines (0 through 15).

7. login local
   - Configures the device to use its local user database for authentication at login.
   - This ensures that only users with valid credentials stored on the device can access it.

8. ping ip-address
   - Sends an Internet Control Message Protocol (ICMP) Echo Request to the specified IP address.
   - Used to test connectivity between the device and a remote host.
   - Example: `ping 192.168.1.1`

9. show ip ssh
   - Displays the version and configuration data for SSH on the device.
   - This includes the SSH version, authentication timeout, and retries.

10. show running-config
    - Displays the active configuration file currently running on the device.
    - This includes all configured settings, such as interfaces, routing protocols, and security configurations.

11. show ssh
    - Displays the status of SSH server connections on the device.
    - This includes details about active SSH sessions, such as the username, IP address, and session state.

12. ssh [-l user-id] {ip-address | host-name}
    - Starts an encrypted SSH session with a remote networking device.
    - The `-l` option specifies the username to use for the connection.
    - Example: `ssh -l admin 192.168.1.1` connects to the device at 192.168.1.1 using the username "admin."

13. telnet ip-address
    - Starts the terminal emulation program to access a remote device over the network using Telnet.
    - Telnet is not secure and transmits data, including passwords, in plain text.
    - Example: `telnet 192.168.1.1`

14. transport input {all | none [ssh] [telnet]}
    - Defines which protocols (SSH, Telnet, or both) can be used to connect to a specific line on the device.
    - Example: `transport input ssh` allows only SSH connections to the VTY lines.

15. username name privilege privilege-level secret password
    - Creates a local username and encrypted password pair and assigns a privilege level to the user.
    - The privilege level determines the commands the user can execute (e.g., level 15 is full access).
    - Example: `username admin privilege 15 secret mypassword` creates a user "admin" with full access and the password "mypassword."