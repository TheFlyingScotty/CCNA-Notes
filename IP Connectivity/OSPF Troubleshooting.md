
Related: [[OSPF]]
## Cisco Recommended Actions to Debug OSPF:



  Please note: At each step of the troubleshooting process, you should determine whether any changes you make resolve the problem.  display the OSPF neighbor table and verify if any routers has formed relationships. This may seem obvious but don't get caught out with the changed 3 things now it works but I cant document what actually fixed it ect..

1. Verify OSPF Configuration:
   - Use the `show running-config` command to ensure OSPF is properly configured on all relevant interfaces and areas.

2. Check OSPF Neighbor Relationships:
   - Use the `show ip ospf neighbor` command to verify that OSPF neighbors are forming correctly and are in the appropriate state (e.g., FULL or 2-WAY).

3. Verify OSPF Interface Settings:
   - Use the `show ip ospf interface` command to check OSPF settings on interfaces, such as area assignments, network types, and hello/dead timers.

4. Check OSPF Routes in the Routing Table:
   - Use the `show ip route ospf` command to verify that OSPF routes are being learned and installed in the routing table.

5. Examine the OSPF Database:
   - Use the `show ip ospf database` command to ensure that LSAs (Link State Advertisements) are being received and processed correctly.

6. Debug OSPF Adjacency Formation:
   - Use the `debug ip ospf adj` command to troubleshoot issues with OSPF neighbor relationships and adjacency formation.

7. Debug OSPF Packets:
   - Use the `debug ip ospf packet` command to monitor OSPF packets (e.g., Hello, DBD, LSR, LSU, LSAck) being sent and received.

8. Debug OSPF Events:
   - Use the `debug ip ospf events` command to track significant OSPF events, such as state changes and LSA updates.

9. Verify OSPF Timers:
   - Ensure that OSPF hello and dead timers match on neighboring routers using the `show ip ospf interface` command.

10. Check OSPF Authentication:
    - Verify that OSPF authentication (if configured) is consistent across all routers using the `show running-config` command.

11. Verify OSPF Area Configuration:
    - Ensure that OSPF areas are correctly configured and that backbone area (Area 0) connectivity is maintained.

12. Check for OSPF Network Type Mismatches:
    - Use the `show ip ospf interface` command to ensure that OSPF network types (e.g., broadcast, point-to-point) are consistent between neighbors.

13. Verify MTU Settings:
    - Ensure that the MTU settings match on OSPF neighbors to avoid adjacency issues.

14. Check for Route Filtering:
    - Verify that route filtering (e.g., distribute lists, route maps) is not unintentionally blocking OSPF routes.

15. Use Conditional Debugging:
    - Use the `debug ip ospf` command with access lists to limit debugging output to specific interfaces or neighbors.

16. Capture Logs for Analysis:
    - Use logging commands (e.g., `logging buffered`) to capture debug output for further analysis.

17. Disable Debugging When Done:
    - Use the `undebug all` or `no debug all` command to stop debugging and prevent excessive CPU usage.

18. Use Packet Capture Tools:
    - If necessary, use packet capture tools (e.g., Wireshark) to analyze OSPF traffic in detail.

19. Consult Cisco Documentation:
    - Refer to Cisco's official OSPF troubleshooting guides and documentation for additional recommendations and best practices.