Related: [[Local Route]],[[IP Connectivity]][[Connected Route]],[[Static Route]]

### Connected Route

**Definition**: A connected route represents a network that is directly connected to one of the router's interfaces. These routes are automatically added to the routing table when an interface is configured with an IP address and is in the "up" state.

**Use Case**: Connected routes are essential for the router to recognize and route traffic to networks that are directly attached to its interfaces. They are automatically added to the routing table and do not require manual configuration.

### Example of a Connected Route

When you configure an IP address on an interface and bring the interface up, the router automatically adds a connected route for the network associated with that IP address. For example, if you configure the IP address `192.168.1.1/24` on the `GigabitEthernet0/0` interface, the router will add a connected route for the `192.168.1.0/24` network.

### Adding a Connected Route Using CLI

Connected routes are automatically added when you assign an IP address to an interface and bring the interface up. Here is how you can configure an IP address on an interface, which will result in the creation of a connected route:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Enter Interface Configuration Mode**:
    
    Router(config)# interface GigabitEthernet0/0
    
3. **Assign an IP Address to the Interface**:
    
    Router(config-if)# ip address 192.168.1.1 255.255.255.0
    
4. **Enable the Interface**:
    
    Router(config-if)# no shutdown
    
5. **Exit Interface Configuration Mode**:
    
    Router(config-if)# exit
    
6. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### Verification

To verify that the connected route has been added, you can use the `show ip route` command:

Router# show ip route

You should see an entry similar to this in the routing table:

C    192.168.1.0/24 is directly connected, GigabitEthernet0/0

This entry indicates that the `192.168.1.0/24` network is a connected route, directly connected to the `GigabitEthernet0/0` interface.