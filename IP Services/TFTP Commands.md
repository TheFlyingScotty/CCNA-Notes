Related: [[TFTP]]

1. configure terminal
   - Enters global configuration mode from privileged EXEC mode.
   - This mode allows you to configure global settings for the device, such as interfaces, routing protocols, and security features.

2. copy running-config {rcp | startup-config | tftp | device:filename}
   - Copies the device's running configuration file to another destination.
   - Options:
     - `rcp`: Copies the configuration to a remote server using the Remote Copy Protocol.
     - `startup-config`: Saves the running configuration to the startup configuration in NVRAM.
     - `tftp`: Copies the configuration to a TFTP server.
     - `device:filename`: Saves the configuration to a specific file on a local or remote device.
   - Example: `copy running-config tftp` saves the current configuration to a TFTP server.

3. copy tftp {running-config | startup-config | device:filename}
   - Copies a file from a TFTP server to another destination on the device.
   - Options:
     - `running-config`: Loads a configuration file from the TFTP server into the running configuration.
     - `startup-config`: Loads a configuration file from the TFTP server into the startup configuration.
     - `device:filename`: Copies the file to a specific location on the device.
   - Example: `copy tftp startup-config` restores a configuration file from a TFTP server to the startup configuration.

4. enable
   - Enters privileged EXEC mode from user EXEC mode.
   - Privileged EXEC mode provides access to all device commands, including configuration, debugging, and monitoring commands.

5. end
   - Exits configuration mode and returns to privileged EXEC mode.
   - This command is used to quickly exit any configuration sub-mode and return to the main privileged EXEC prompt.

6. erase startup-config
   - Deletes the startup configuration file stored in non-volatile random access memory (NVRAM).
   - This resets the device to its factory default configuration after a reboot.
   - Example: `erase startup-config` removes all saved configurations.

7. exit
   - Exits one level in the menu structure.
   - For example, if you are in interface configuration mode, this command will return you to global configuration mode.

8. hostname host-name
   - Sets the device's hostname (name used to identify the device).
   - Example: `hostname Router1` sets the device's name to "Router1."

9. ipconfig /dg ip-address
   - Used in NetSim to assign a default gateway IP address to a workstation interface.
   - Example: `ipconfig /dg 192.168.1.1` sets the default gateway to 192.168.1.1.

10. ipconfig /ip ip-address subnet-mask
    - Used in NetSim to assign an IP address and subnet mask to a workstation interface.
    - Example: `ipconfig /ip 192.168.1.10 255.255.255.0` assigns the IP address 192.168.1.10 with a subnet mask of 255.255.255.0.

11. ping ip-address
    - Sends an Internet Control Message Protocol (ICMP) Echo Request to the specified IP address.
    - Used to test connectivity between the device and a remote host.
    - Example: `ping 192.168.1.1` tests connectivity to the IP address 192.168.1.1.

12. show startup-config
    - Displays the backup configuration file stored in NVRAM.
    - This file contains the configuration that will be loaded when the device is restarted.

13. show tftp-configs
    - Used in NetSim to display a list of files copied using TFTP and stored on a PC.
    - This command helps verify the files available for transfer or restoration.