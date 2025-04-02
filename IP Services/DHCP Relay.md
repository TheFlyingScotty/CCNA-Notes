Related: [[DHCP]],[[DHCP Relay Commands]]

Definition:
DHCP Relay is a network feature that allows DHCP requests from clients in one subnet to be forwarded to a DHCP server located in a different subnet. This enables centralized DHCP servers to provide IP address assignments and configuration to clients across multiple subnets.

Explanation:
In networks where the DHCP server is not on the same subnet as the clients, a DHCP relay agent is required. The relay agent listens for DHCP broadcast messages from clients and forwards them as unicast messages to the DHCP server. The server processes the request and sends the response back to the relay agent, which then forwards it to the client.

Key Features:
1. **Cross-Subnet Communication**:
   - Allows DHCP servers to serve clients in subnets where they are not directly connected.
2. **Centralized Management**:
   - Enables the use of a single DHCP server to manage IP address assignments for multiple subnets.
3. **Relay Agent Configuration**:
   - The relay agent is typically configured on a router or Layer 3 switch.

Use Cases:
1. **Large Networks**:
   - Used in enterprise networks with multiple subnets to centralize DHCP services.
2. **Simplified Administration**:
   - Reduces the need for deploying a DHCP server in every subnet.

DHCP Relay Process:
1. The client sends a DHCPDISCOVER broadcast message.
2. The relay agent intercepts the broadcast and forwards it to the DHCP server as a unicast message.
3. The DHCP server processes the request and sends a response (e.g., DHCPOFFER) back to the relay agent.
4. The relay agent forwards the response to the client.

Configuration Example:
On a Cisco router, the `ip helper-address <DHCP-server-IP>` command is used to configure a DHCP relay agent.

Summary:
DHCP Relay enables centralized DHCP servers to provide IP address assignments and configuration to clients across multiple subnets, simplifying network management in large or segmented networks.