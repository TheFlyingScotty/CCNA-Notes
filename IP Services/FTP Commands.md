Related: [[FTP]]

1. configure terminal
   - Enters global configuration mode from privileged EXEC mode.
   - This mode allows you to configure global settings for the device, including FTP-related configurations.
   - Example: `Router# configure terminal`

2. ip ftp username <username>
   - Configures the username for FTP authentication when accessing an FTP server.
   - Example: `ip ftp username admin` sets the FTP username to "admin."

3. ip ftp password <password>
   - Configures the password for FTP authentication when accessing an FTP server.
   - Example: `ip ftp password mypassword` sets the FTP password to "mypassword."

4. copy running-config ftp
   - Copies the running configuration file to an FTP server.
   - Example: `copy running-config ftp` prompts for the FTP server address and saves the configuration file.

5. copy ftp running-config
   - Copies a configuration file from an FTP server to the running configuration on the device.
   - Example: `copy ftp running-config` retrieves a configuration file from the FTP server and applies it to the running configuration.

6. copy startup-config ftp
   - Copies the startup configuration file to an FTP server.
   - Example: `copy startup-config ftp` prompts for the FTP server address and saves the startup configuration file.

7. copy ftp startup-config
   - Copies a configuration file from an FTP server to the startup configuration on the device.
   - Example: `copy ftp startup-config` retrieves a configuration file from the FTP server and saves it as the startup configuration.

8. copy ftp flash:<filename>
   - Copies a file from an FTP server to the device's flash memory.
   - Example: `copy ftp flash:ios-image.bin` downloads an IOS image file from the FTP server to the device's flash memory.

9. copy flash:<filename> ftp
   - Copies a file from the device's flash memory to an FTP server.
   - Example: `copy flash:ios-image.bin ftp` uploads an IOS image file from the device's flash memory to the FTP server.

10. ip ftp source-interface <interface>
    - Specifies the source interface for FTP traffic.
    - Example: `ip ftp source-interface GigabitEthernet0/0` ensures FTP traffic originates from the GigabitEthernet0/0 interface.

11. debug ip ftp
    - Enables debugging for FTP operations to troubleshoot issues.
    - Example: `debug ip ftp` displays detailed information about FTP transactions.

12. show running-config | include ftp
    - Displays FTP-related configurations in the running configuration.
    - Example: `show running-config | include ftp` filters and shows only lines related to FTP settings.

13. show ip ftp
    - Displays the current FTP username, password, and source interface configuration.
    - Example: `show ip ftp` provides details about the FTP settings on the device.

14. no ip ftp username
    - Removes the configured FTP username.
    - Example: `no ip ftp username` clears the FTP username setting.

15. no ip ftp password
    - Removes the configured FTP password.
    - Example: `no ip ftp password` clears the FTP password setting.

16. no ip ftp source-interface
    - Removes the configured source interface for FTP traffic.
    - Example: `no ip ftp source-interface` resets the FTP source interface to the default setting.