Related: [[IP Connectivity]]

Definition of EGP:
Exterior Gateway Protocol (EGP) is a type of routing protocol used to exchange routing information between different autonomous systems (ASes) on the internet. EGPs are designed to handle routing between large, disparate networks that are managed by different organizations.

Explanation:
EGP is used to facilitate communication and routing between autonomous systems, which are collections of IP networks and routers under the control of a single organization that presents a common routing policy to the internet. EGPs ensure that data can be routed efficiently and reliably across the global internet by sharing routing information between ASes.

Versions of EGP:

1. EGP (Original EGP):
   - **Definition**: The original Exterior Gateway Protocol, defined in RFC 904.
   - **Explanation**: EGP was one of the first protocols used to exchange routing information between different autonomous systems. It is a distance-vector protocol that uses a simple mechanism to share reachability information. However, EGP has several limitations, including a lack of support for complex routing policies and scalability issues.
   - **Use Case**: EGP was used in the early days of the internet to connect different autonomous systems. It has since been largely replaced by more advanced protocols like BGP.

2. BGP (Border Gateway Protocol):
   - **Definition**: The Border Gateway Protocol, defined in RFC 4271, is the successor to the original EGP and is the de facto standard for inter-AS routing on the internet.
   - **Explanation**: BGP is a path-vector protocol that uses a more sophisticated mechanism to exchange routing information between ASes. It supports complex routing policies, scalability, and provides mechanisms for route aggregation, route filtering, and policy-based routing. BGP is capable of handling the vast and dynamic nature of the global internet.
   - **Use Case**: BGP is used by internet service providers (ISPs), large enterprises, and other organizations to manage routing between their networks and other ASes. It is essential for maintaining the stability and efficiency of the global internet.

Example Configuration for BGP:
1. Enter global configuration mode:
   configure terminal

2. Enable BGP routing and specify the AS number:
   router bgp <AS-number>

3. Configure the networks to be advertised:
   network <network> mask <subnet-mask>

4. Configure BGP neighbors (peers):
   neighbor <neighbor-IP> remote-as <neighbor-AS>

5. Exit BGP configuration mode:
   exit

Example:
To configure BGP on a router with AS number 65001, advertising network 192.168.1.0/24, and peering with a neighbor at 10.0.0.2 in AS 65002:

configure terminal
router bgp 65001
network 192.168.1.0 mask 255.255.255.0
neighbor 10.0.0.2 remote-as 65002
exit

Summary:
- **EGP**: A type of routing protocol used to exchange routing information between different autonomous systems.
- **Original EGP**: An early distance-vector protocol for inter-AS routing, now largely obsolete.
- **BGP**: The Border Gateway Protocol, a path-vector protocol and the de facto standard for inter-AS routing on the internet, supporting complex routing policies and scalability.