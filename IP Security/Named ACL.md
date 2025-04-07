Related: [[access control lists (ACL)]]

Definition:  
Named Access Control Lists (Named ACLs) are a type of ACL that allows administrators to assign a descriptive name to an ACL instead of using a numeric identifier. Named ACLs can be either a [[Standard ACL]] or [[Extended ACL]] and provide better readability and easier management compared to numbered ACLs.

Explanation:  
Named ACLs operate at Layer 3 (Network) and Layer 4 (Transport) of the OSI model, depending on whether they are standard or extended. They allow administrators to create, modify, and delete specific rules within the ACL without having to recreate the entire list, which is a limitation of numbered ACLs. Named ACLs are especially useful in large networks where descriptive names improve clarity and organization.

Key Features:

1. **Descriptive Names**:
    - ACLs are identified by a name instead of a number, making them easier to understand and manage.
2. **Standard or Extended**:
    - Named ACLs can be used for both standard (source-based filtering) and extended (protocol, port, and destination-based filtering) purposes.
3. **Editable Rules**:
    - Individual rules within a named ACL can be added, modified, or removed without affecting the entire ACL.

Use Cases:

1. **Improved Management**:
    - Useful in large networks where descriptive names make ACLs easier to identify and manage.
2. **Granular Control**:
    - Provides the same functionality as standard or extended ACLs but with added flexibility for editing rules.

Example:  
To create a named extended ACL called "BLOCK_HTTP" that denies HTTP traffic from 192.168.1.0/24 to 10.0.0.0/24:

1. Create the ACL:  
    ip access-list extended BLOCK_HTTP  
    deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80  
    permit ip any any
    
    - The first line creates the named ACL "BLOCK_HTTP."
    - The second line denies HTTP traffic from 192.168.1.0/24 to 10.0.0.0/24.
    - The third line permits all other traffic.
2. Apply the ACL to an interface:  
    interface GigabitEthernet0/0  
    ip access-group BLOCK_HTTP in
    
    - This applies the named ACL to inbound traffic on the specified interface.

Summary:  
Named ACLs provide the same functionality as numbered ACLs but are easier to manage and modify due to their descriptive names and editable rules. They are ideal for large or complex networks where clarity and flexibility are important.