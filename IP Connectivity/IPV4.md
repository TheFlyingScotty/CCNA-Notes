Related: 

### Definition of an IPv4 Address

An IPv4 (Internet Protocol version 4) address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication. It serves two main functions: identifying the host or network interface and providing the location of the host in the network.

### Construction of an IPv4 Address

An IPv4 address is a 32-bit number, typically represented in decimal format as four octets (8-bit segments) separated by periods. Each octet can range from 0 to 255.

#### Example:

192.168.1.1

### Structure:

1. **Binary Representation**:
    
    - An IPv4 address is composed of 32 bits.
    - Example: `11000000.10101000.00000001.00000001` (binary representation of `192.168.1.1`).
2. **Decimal Representation**:
    
    - Each octet (8 bits) is converted to its decimal form.
    - Example: `192.168.1.1`.

### Components:

1. **Network Portion**:
    
    - The part of the IP address that identifies the specific network on which a device is located.
    - Determined by the subnet mask.
2. **Host Portion**:
    
    - The part of the IP address that identifies the specific device (host) on the network.
    - Determined by the subnet mask.

### Subnet Mask:

A subnet mask is used to divide the IP address into the network and host portions. It is also a 32-bit number, typically represented in the same dotted-decimal format as the IP address.

#### Example:

255.255.255.0

### [Classes of IPv4 Addresses:]

IPv4 addresses are divided into five classes (A, B, C, D, E) based on the leading bits of the address:

1. **Class A**:
    
    - Range: `1.0.0.0` to `126.255.255.255`
    - Default Subnet Mask: `255.0.0.0`
    - Network/Host: `8 bits network / 24 bits host`
2. **Class B**:
    
    - Range: `128.0.0.0` to `191.255.255.255`
    - Default Subnet Mask: `255.255.0.0`
    - Network/Host: `16 bits network / 16 bits host`
3. **Class C**:
    
    - Range: `192.0.0.0` to `223.255.255.255`
    - Default Subnet Mask: `255.255.255.0`
    - Network/Host: `24 bits network / 8 bits host`
4. **Class D**:
    
    - Range: `224.0.0.0` to `239.255.255.255`
    - Used for multicast.
5. **Class E**:
    
    - Range: `240.0.0.0` to `255.255.255.255`
    - Reserved for experimental use.

### Special IPv4 Addresses:

1. **Loopback Address**:
    
    - `127.0.0.1` (used for testing and diagnostics).
2. **Broadcast Address**:
    
    - `255.255.255.255` (used to send data to all hosts on a network).
3. **Private Addresses**:
    
    - Not routable on the internet, used within private networks.
    - Ranges: `10.0.0.0` to `10.255.255.255`, `172.16.0.0` to `172.31.255.255`, `192.168.0.0` to `192.168.255.255`.

### Summary:

An IPv4 address is a 32-bit number used to identify devices on a network, divided into network and host portions by a subnet mask, and represented in a dotted-decimal format. It is essential for routing and addressing in IP-based networks.