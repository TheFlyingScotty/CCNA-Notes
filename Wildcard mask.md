### Wildcard Mask

**Definition**: A wildcard mask is a 32-bit number used in networking to specify which bits of an IP address should be ignored during the routing process. It is commonly used in[[ access control lists (ACLs)]] and routing protocols like [[OSPF]] to match a range of IP addresses. In a wildcard mask, a bit value of `0` means that the corresponding bit in the IP address must match exactly, while a bit value of `1` means that the corresponding bit can be either `0` or `1`.

### Converting a CIDR/Subnet Mask to a Wildcard Mask

To convert a subnet mask to a wildcard mask, you simply invert the bits of the subnet mask. This means changing all `0`s to `1`s and all `1`s to `0`s.

#### Steps to Convert:

1. **Write down the subnet mask in binary format.**
2. **Invert the bits of the subnet mask to get the wildcard mask.**
3. **Convert the binary wildcard mask back to decimal format.**

### Example Conversion

#### Example 1: Subnet Mask `255.255.255.0` (CIDR `/24`)

1. **Subnet Mask in Binary**:
    
    255.255.255.0 = 11111111.11111111.11111111.00000000
    
2. **Invert the Bits**:
    
    Wildcard Mask = 00000000.00000000.00000000.11111111
    
3. **Wildcard Mask in Decimal**:
    
    Wildcard Mask = 0.0.0.255
    

#### Example 2: Subnet Mask `255.255.255.240` (CIDR `/28`)

1. **Subnet Mask in Binary**:
    
    255.255.255.240 = 11111111.11111111.11111111.11110000
    
2. **Invert the Bits**:
    
    Wildcard Mask = 00000000.00000000.00000000.00001111
    
3. **Wildcard Mask in Decimal**:
    
    Wildcard Mask = 0.0.0.15
    

### Summary

- **Subnet Mask**: `255.255.255.0` (CIDR `/24`)
    
    - **Wildcard Mask**: `0.0.0.255`
- **Subnet Mask**: `255.255.255.240` (CIDR `/28`)
    
    - **Wildcard Mask**: `0.0.0.15`

### Usage in CLI

When configuring ACLs or routing protocols, you use the wildcard mask to specify which bits of the IP address to match.

#### Example in ACL Configuration:

Router(config)# access-list 10 permit 192.168.1.0 0.0.0.255

This ACL entry permits traffic from any IP address in the `192.168.1.0/24` network.

# Configuring a ospf network, how to work how what wildcard i need?

To configure OSPF to advertise both the `203.0.113.0/30` network and the `203.0.113.4/30` network, you need to determine the appropriate wildcard mask.

### Step-by-Step Process

1. **Identify the Networks**:
    
    - `203.0.113.0/30`
    - `203.0.113.4/30`
2. **Determine the Subnet Mask**:
    
    - Both networks use a `/30` subnet mask, which is `255.255.255.252`.
3. **Calculate the Wildcard Mask**:
    
    - The wildcard mask is the inverse of the subnet mask.
    - Subnet Mask: `255.255.255.252`
    - Wildcard Mask: `0.0.0.3`
4. **Determine the Network Range**:
    
    - The `203.0.113.0/30` network includes IP addresses from `203.0.113.0` to `203.0.113.3`.
    - The `203.0.113.4/30` network includes IP addresses from `203.0.113.4` to `203.0.113.7`.
5. **Summarize the Networks**:
    
    - Both networks can be summarized as `203.0.113.0/29`.
    - Subnet Mask for `/29`: `255.255.255.248`
    - Wildcard Mask for `/29`: `0.0.0.7`

### Configuration Example

To configure OSPF to advertise both networks using the summarized network and wildcard mask, you can use the following commands:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Enter OSPF Configuration Mode**:
    
    Router(config)# router ospf 1
    
3. **Advertise the Summarized Network**:
    
    Router(config-router)# network 203.0.113.0 0.0.0.7 area 0
    
4. **Exit OSPF Configuration Mode**:
    
    Router(config-router)# exit
    
5. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### Summary

- **Networks to Advertise**: `203.0.113.0/30` and `203.0.113.4/30`
- **Summarized Network**: `203.0.113.0/29`
- **Wildcard Mask**: `0.0.0.7`

By using the summarized network `203.0.113.0/29` with the wildcard mask `0.0.0.7`, OSPF will advertise both the `203.0.113.0/30` and `203.0.113.4/30` networks.