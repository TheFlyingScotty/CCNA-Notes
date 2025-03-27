
Related: [[HSRP]]
HSRP States:

1. Init (Initialization):
   - **Definition**: This is the starting state of an HSRP-enabled router.
   - **Explanation**: The router is not yet participating in HSRP. It is waiting for the HSRP configuration to be completed or for an interface to become active.
   - **Use Case**: The router is in this state when HSRP is first enabled or when the interface is down.

2. Learn:
   - **Definition**: The router is waiting to learn the virtual IP address from an active router.
   - **Explanation**: In this state, the router does not yet know the virtual IP address and has not seen any HSRP hello messages from the active router.
   - **Use Case**: The router transitions to this state when it is configured for HSRP but has not yet received the necessary information to participate.

3. Listen:
   - **Definition**: The router knows the virtual IP address but is not the active or standby router.
   - **Explanation**: The router listens for HSRP hello messages from the active and standby routers to monitor their status.
   - **Use Case**: The router is a backup participant in the HSRP group but is not currently responsible for forwarding traffic.

4. Speak:
   - **Definition**: The router is actively participating in the HSRP election process.
   - **Explanation**: The router sends HSRP hello messages and participates in the election to determine the active and standby routers.
   - **Use Case**: The router transitions to this state when it is competing to become the active or standby router.

5. Standby:
   - **Definition**: The router is the backup to the active router and will take over if the active router fails.
   - **Explanation**: The standby router monitors the active router by listening for hello messages. If the active router becomes unavailable, the standby router transitions to the active state.
   - **Use Case**: The router is ready to take over as the active router in case of a failure, ensuring high availability.

6. Active:
   - **Definition**: The router is currently forwarding traffic for the virtual IP address.
   - **Explanation**: The active router is responsible for handling all traffic sent to the virtual IP address. It sends periodic hello messages to inform other routers in the HSRP group of its status.
   - **Use Case**: The router is the primary device in the HSRP group, ensuring uninterrupted traffic flow for the virtual IP address.

Summary:
- **Init**: Starting state; HSRP is not yet active.
- **Learn**: Waiting to learn the virtual IP address.
- **Listen**: Knows the virtual IP but is not active or standby.
- **Speak**: Participating in the election process.
- **Standby**: Backup to the active router, ready to take over.
- **Active**: Primary router forwarding traffic for the virtual IP address.