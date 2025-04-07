
Related:[[access control lists (ACL)]]


1. access-list <number> {permit | deny} <protocol> <source> <wildcard-mask> <destination> <wildcard-mask> [eq <port>]
   - Creates a numbered ACL with a specific rule to permit or deny traffic.
   - Example: `access-list 100 deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80` denies HTTP traffic from 192.168.1.0/24 to 10.0.0.0/24.

2. ip access-list {standard | extended} <name>
   - Creates a named ACL and enters ACL configuration mode.
   - Example: `ip access-list extended BLOCK_HTTP` creates a named extended ACL called "BLOCK_HTTP."

3. {permit | deny} <protocol> <source> <wildcard-mask> <destination> <wildcard-mask> [eq <port>]
   - Adds a rule to a named ACL to permit or deny traffic.
   - Example: `deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80` denies HTTP traffic in a named ACL.

4. no access-list <number>
   - Deletes a numbered ACL.
   - Example: `no access-list 100` removes ACL 100.

5. no ip access-list <name>
   - Deletes a named ACL.
   - Example: `no ip access-list BLOCK_HTTP` removes the named ACL "BLOCK_HTTP."

6. ip access-group <number | name> {in | out}
   - Applies an ACL to an interface in the inbound or outbound direction.
   - Example: `ip access-group 100 in` applies ACL 100 to inbound traffic on an interface.

7. show access-lists
   - Displays all configured ACLs and their rules.
   - Example: `show access-lists` lists all ACLs on the device.

8. show ip access-lists
   - Displays only IP-based ACLs and their rules.
   - Example: `show ip access-lists` lists all IP ACLs.

9. show running-config | include access-list
   - Displays ACL-related configurations in the running configuration.
   - Example: `show running-config | include access-list` filters and shows only ACL lines.

10. clear access-list counters <number | name>
    - Clears the hit counters for a specific ACL.
    - Example: `clear access-list counters 100` resets the counters for ACL 100.

11. access-class <number | name> {in | out}
    - Applies an ACL to control access to VTY lines for Telnet or SSH.
    - Example: `access-class 10 in` applies ACL 10 to inbound VTY access.

12. remark <text>
    - Adds a comment to an ACL for documentation purposes.
    - Example: `access-list 100 remark Block HTTP traffic` adds a comment to ACL 100.

13. sequence <number> {permit | deny} <protocol> <source> <wildcard-mask> <destination> <wildcard-mask> [eq <port>]
    - Adds a rule to a named ACL with a specific sequence number.
    - Example: `sequence 10 deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80` adds a rule with sequence number 10.

14. no sequence <number>
    - Removes a specific rule from a named ACL by its sequence number.
    - Example: `no sequence 10` removes the rule with sequence number 10.

15. log
    - Appends logging to an ACL rule to track matches.
    - Example: `access-list 100 deny tcp 192.168.1.0 0.0.0.255 10.0.0.0 0.0.0.255 eq 80 log` logs matches for the rule.

16. ip access-list resequence <name> <starting-sequence> <increment>
    - Resequences the rules in a named ACL.
    - Example: `ip access-list resequence BLOCK_HTTP 10 10` starts the sequence at 10 and increments by 10.

17. interface <type> <number>
    - Enters interface configuration mode to apply an ACL.
    - Example: `interface GigabitEthernet0/0` enters configuration mode for the GigabitEthernet0/0 interface.

18. ip access-group <number | name> {in | out}
    - Applies an ACL to an interface in the inbound or outbound direction.
    - Example: `ip access-group BLOCK_HTTP in` applies the named ACL "BLOCK_HTTP" to inbound traffic.

19. access-list <number> permit any
    - Adds a rule to allow all traffic.
    - Example: `access-list 100 permit any` permits all traffic in ACL 100.

20. access-list <number> deny any
    - Adds a rule to block all traffic.
    - Example: `access-list 100 deny any` denies all traffic in ACL 100.

21. ip access-list standard <name>
    - Creates a named standard ACL.
    - Example: `ip access-list standard ALLOW_LOCAL` creates a named standard ACL called "ALLOW_LOCAL."

22. permit <source> <wildcard-mask>
    - Adds a rule to a standard ACL to permit traffic from a specific source.
    - Example: `permit 192.168.1.0 0.0.0.255` permits traffic from 192.168.1.0/24.

23. deny <source> <wildcard-mask>
    - Adds a rule to a standard ACL to deny traffic from a specific source.
    - Example: `deny 192.168.1.0 0.0.0.255` denies traffic from 192.168.1.0/24.

24. ip access-list extended <name>
    - Creates a named extended ACL.
    - Example: `ip access-list extended BLOCK_WEBSERVICES` creates a named extended ACL called "BLOCK_WEBSERVICES."

25. access-list <number> permit ip any any
    - Adds a rule to allow all IP traffic.
    - Example: `access-list 100 permit ip any any` permits all IP traffic in ACL 100.