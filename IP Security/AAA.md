Related [[IP Security]]

Definition:  
AAA stands for Authentication, Authorization, and Accounting. It is a framework used to control access to network resources, enforce policies, and track user activities. AAA ensures secure access to devices and services by verifying user identities, determining their permissions, and logging their actions.

Explanation:  
AAA is a critical component of network security and is commonly implemented on network devices such as routers, switches, and firewalls. It works with protocols like RADIUS (Remote Authentication Dial-In User Service) and TACACS+ (Terminal Access Controller Access-Control System Plus) to provide centralized management of user access and activity.

Key Components:

1. Authentication:
    
    - Verifies the identity of users or devices attempting to access the network.
    - Ensures that only authorized users can log in.
    - Example: A user enters a username and password to access a router.
2. Authorization:
    
    - Determines what actions or resources a user is allowed to access after authentication.
    - Enforces policies based on user roles or permissions.
    - Example: A network administrator is allowed to configure devices, while a regular user can only view settings.
3. Accounting:
    
    - Tracks and logs user activities, such as login times, commands executed, and resources accessed.
    - Provides an audit trail for monitoring and troubleshooting.
    - Example: Logging the commands entered by a user during a session.

Use Cases:

1. Network Device Access:
    - Secures access to routers, switches, and firewalls by requiring authentication and enforcing role-based permissions.
2. VPN Access:
    - Ensures that only authorized users can establish VPN connections and access internal resources.
3. Auditing and Compliance:
    - Tracks user activities for compliance with security policies and regulatory requirements.

Protocols Used:

1. RADIUS:
    - Combines authentication and authorization into a single process.
    - Commonly used for remote access and wireless networks.
2. TACACS+:
    - Separates authentication, authorization, and accounting processes.
    - Provides more granular control and is commonly used for device management.

Example Configuration:  
To configure AAA on a Cisco device:

1. Enable AAA:  
    aaa new-model
    
    - Activates the AAA framework on the device.
2. Configure a RADIUS or TACACS+ server:  
    radius-server host 192.168.1.100 key mysecret
    
    - Specifies the RADIUS server and shared secret for authentication.
3. Apply AAA to login:  
    aaa authentication login default group radius local
    
    - Configures the device to use RADIUS for login authentication, with local authentication as a fallback.

Summary:  
AAA (Authentication, Authorization, and Accounting) is a framework for securing access to network resources, enforcing policies, and tracking user activities. It ensures that only authorized users can access the network, defines what they can do, and logs their actions for auditing and compliance.