# Network Troubleshooting

## Complete Professional Notes

---

# Table of Contents

1. Introduction to Network Troubleshooting
2. Importance of Network Troubleshooting
3. Networking Troubleshooting Methodology
4. OSI Model and Troubleshooting
5. Common Network Problems
6. Physical Layer Troubleshooting
7. IP Addressing Issues
8. DNS Troubleshooting
9. Gateway and Routing Problems
10. Connectivity Troubleshooting
11. Performance Troubleshooting
12. Packet Loss and Latency
13. Network Troubleshooting Tools
14. ping Command
15. traceroute and tracepath
16. ip Command
17. ifconfig Command
18. netstat Command
19. ss Command
20. nslookup Command
21. dig Command
22. host Command
23. arp Command
24. tcpdump Command
25. Wireshark
26. curl Command
27. wget Command
28. nc (Netcat)
29. telnet Command
30. mtr Command
31. Diagnosing Slow Networks
32. Diagnosing DNS Issues
33. Diagnosing Routing Problems
34. Diagnosing Firewall Problems
35. Diagnosing Port Issues
36. Linux Log Files for Networking
37. Troubleshooting SSH Connectivity
38. Troubleshooting Web Servers
39. Troubleshooting VPN Connections
40. Enterprise Troubleshooting Practices
41. Best Practices
42. Interview Questions and Answers
43. Practical Labs
44. Conclusion

---

# 1. Introduction to Network Troubleshooting

Network troubleshooting is the process of identifying, analyzing, and resolving network-related problems.

Modern IT infrastructure depends heavily on reliable networks for:

* Internet access
* Cloud computing
* Communication
* Servers
* Databases
* Applications
* Virtualization
* DevOps environments

When network problems occur, services may become:

* Slow
* Unreachable
* Unstable
* Completely unavailable

Network troubleshooting is one of the most important skills for:

* Linux Administrators
* DevOps Engineers
* Network Engineers
* Cloud Engineers
* Cybersecurity Professionals

---

# 2. Importance of Network Troubleshooting

Proper troubleshooting helps:

* Reduce downtime
* Improve performance
* Identify security issues
* Restore connectivity
* Prevent future problems
* Maintain business operations

---

# 3. Networking Troubleshooting Methodology

Professional troubleshooting follows a structured process.

---

## Standard Methodology

1. Identify the problem
2. Gather information
3. Establish a theory
4. Test the theory
5. Implement solution
6. Verify functionality
7. Document findings

---

# 4. OSI Model and Troubleshooting

The OSI model helps isolate problems.

| Layer   | Function     |
| ------- | ------------ |
| Layer 7 | Application  |
| Layer 6 | Presentation |
| Layer 5 | Session      |
| Layer 4 | Transport    |
| Layer 3 | Network      |
| Layer 2 | Data Link    |
| Layer 1 | Physical     |

---

## Example

| Problem            | Likely Layer      |
| ------------------ | ----------------- |
| Cable disconnected | Physical          |
| Wrong IP address   | Network           |
| DNS failure        | Application       |
| Firewall block     | Transport/Network |

---

# 5. Common Network Problems

| Problem           | Description                |
| ----------------- | -------------------------- |
| No connectivity   | Cannot reach network       |
| Slow internet     | High latency or congestion |
| DNS failure       | Hostnames not resolving    |
| Packet loss       | Missing packets            |
| Routing issues    | Wrong network path         |
| Firewall blocking | Traffic denied             |
| Port issues       | Service unreachable        |
| VPN issues        | Tunnel failure             |

---

# 6. Physical Layer Troubleshooting

The Physical Layer includes:

* Cables
* Switch ports
* Network cards
* Wireless signals
* Power connections

---

## Common Physical Problems

* Loose cables
* Faulty NIC
* Broken switch port
* Weak Wi-Fi signal
* Hardware failure

---

## Checks

* Verify cable connections
* Check NIC LEDs
* Test another cable
* Verify switch status

---

# 7. IP Addressing Issues

Incorrect IP configuration is a very common problem.

---

## Common Problems

* Wrong IP address
* Wrong subnet mask
* Missing gateway
* Duplicate IP address

---

## Display IP Configuration

```bash
ip addr
```

OR

```bash
ifconfig
```

---

## Check Routing Table

```bash
ip route
```

---

# 8. DNS Troubleshooting

DNS converts domain names into IP addresses.

---

## Common DNS Problems

* Website not opening
* Slow name resolution
* Wrong DNS server
* DNS timeout

---

## Test DNS

```bash
nslookup google.com
```

OR

```bash
dig google.com
```

---

## Check DNS Configuration

```bash
cat /etc/resolv.conf
```
