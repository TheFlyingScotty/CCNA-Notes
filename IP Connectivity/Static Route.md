Related: [[Local Route]],[[IP Connectivity]][[Connected Route]],[[Static Route]],[[A AI explination to static routes I needed]]

**Definition**: A static route is a manually configured route that specifies a fixed path for traffic to reach a particular network or host. Static routes are added to the routing table by the network administrator and do not change unless manually modified.

### Types of Static Routes

1. **Standard Static Route**
2. **Default Static Route**
3. **Floating Static Route**
4. **Host Static Route**

### Why Use Static Routes?

- **Simplicity**: Easy to configure and understand.
- **Control**: Provides precise control over routing paths.
- **Predictability**: Routes do not change unless manually modified.
- **Backup**: Can be used as backup routes with higher administrative distances.

### 1. Standard Static Route

**Definition**: A route to a specific network or host. 
**Use Case**: Used to define a specific path for traffic to reach a particular destination.

**Example Configuration**:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Add the Static Route**:
    
    Router(config)# ip route 192.168.2.0 255.255.255.0 192.168.1.2
    
3. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### 2. Default Static Route

**Definition**: A route that matches all destinations not covered by more specific routes. It is used as a gateway of last resort. **Use Case**: Used to route traffic to an upstream router or the internet when no other route matches, Gateway of last resort.

**Example Configuration**:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Add the Default Route**:
    
    Router(config)# ip route 0.0.0.0 0.0.0.0 192.168.1.1
    
3. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### 3. Floating Static Route

**Definition**: A static route with a higher administrative distance than dynamic routes, used as a backup route. **Use Case**: Used to provide a backup path in case the primary route learned via a dynamic routing protocol fails.

**Example Configuration**:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Add the Floating Static Route**:
    
    Router(config)# ip route 192.168.3.0 255.255.255.0 192.168.1.3 200
    
3. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### 4. Host Static Route

**Definition**: A route to a specific host (single IP address). **Use Case**: Used to route traffic to a specific host.

**Example Configuration**:

1. **Enter Global Configuration Mode**:
    
    Router# configure terminal
    
2. **Add the Host Static Route**:
    
    Router(config)# ip route 192.168.4.1 255.255.255.255 192.168.1.4
    
3. **Exit Global Configuration Mode**:
    
    Router(config)# end
    

### Verification

To verify that the static routes have been added, you can use the `show ip route` command:

Router# show ip route

You should see entries similar to these in the routing table:

**Standard Static Route**:

S    192.168.2.0/24 [1/0] via 192.168.1.2

**Default Static Route**:

S*   0.0.0.0/0 [1/0] via 192.168.1.1

**Floating Static Route**:

S    192.168.3.0/24 [200/0] via 192.168.1.3

**Host Static Route**:

S    192.168.4.1/32 [1/0] via 192.168.1.4

These entries indicate that the routes have been successfully added to the routing table.