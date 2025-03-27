
Related: [[Local Route]],[[IP Connectivity]][[Connected Route]],[[Static Route]]

### Local Route

**Definition**: A local route represents the IP address of the router's own interfaces. It is automatically created by the router when an IP address is assigned to an interface. Local routes are used to route traffic destined for the router itself.

**Use Case**: Local routes are essential for the router to recognize its own IP addresses and handle traffic directed to those addresses. They are automatically added to the routing table and do not require manual configuration.

### Example of a Local Route

When you configure an IP address on an interface, the router automatically adds a local route for that IP address. For example, if you configure the IP address `192.168.1.1` on the `GigabitEthernet0/0` interface, the router will add a local route for `192.168.1.1/32`.

### Adding a Local Route Using CLI

Local routes are automatically added when you assign an IP address to an interface. Here is how you can configure an IP address on an interface, which will result in the creation of a local route:

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

To verify that the local route has been added, you can use the `show ip route` command:

Router# show ip route

You should see an entry similar to this in the routing table:

L    192.168.1.1/32 is directly connected, GigabitEthernet0/0

This entry indicates that the IP address `192.168.1.1` is a local route, directly connected to the `GigabitEthernet0/0` interface.