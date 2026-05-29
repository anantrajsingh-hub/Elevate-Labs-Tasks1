## Task 1: Scan Your Local Network for Open Ports

### Objective
Learn to discover open ports on devices in a local network to understand network exposure using Nmap.

### Methodology
1. Identified local network range using `ip a` on Kali Linux.
2. Executed a TCP SYN Scan using Nmap to discover active hosts and open ports.
3. Command Used: `sudo nmap -sS 10.0.2.0/24 -oN nmap_report.txt`
4. Saved the output into a text file for analysis.

### Scan Results Summary
- **Target Range:** 10.0.2.0/24
- **Active Hosts Found:** 3 hosts up.
- **Open Ports Discovered:** 
  - Port 135/tcp (msrpc)
  - Port 445/tcp (microsoft-ds)
  - Port 903/tcp (iss-console-mgr)
  - Port 7070/tcp (realserver)
  - Port 53/tcp (domain)

---

### Interview Questions & Answers

1. What is an open port?
Answer: An open port is a network port that is actively listening for incoming packets or connections. It indicates that a service or application is running on that port and is ready to communicate.

2. How does Nmap perform a TCP SYN scan?
Answer: A TCP SYN scan (half-open scan) sends a SYN packet to the target port. If the port responds with a SYN/ACK, the port is open, and Nmap immediately sends a RST packet to close the connection before it fully establishes. If it responds with a RST, the port is closed.

#### 3. What risks are associated with open ports?
Answer: Open ports expose services to the network. If those services are misconfigured, outdated, or have unpatched vulnerabilities, attackers can exploit them to gain unauthorized access or cause a Denial of Service (DoS).

4. Explain the difference between TCP and UDP scanning.
Answer: TCP scanning relies on the 3-way handshake and requires connection acknowledgment, making it highly reliable. UDP scanning is connectionless; Nmap sends a UDP packet and assumes the port is open/filtered if no response is received, making it slower and less reliable.

5. How can open ports be secured?
Answer: Close unnecessary ports by disabling unused services.
- Keep the software/services running on those ports updated.
- Implement strict Firewall rules to restrict access.

6. What is a firewall's role regarding ports?
Answer: A firewall acts as a barrier that monitors and filters incoming and outgoing network traffic based on predetermined security rules. It can block unauthorized traffic from reaching open ports.

7. What is a port scan and why do attackers perform it?
Answer: A port scan is a reconnaissance technique used to identify active hosts and open ports on a network. Attackers perform it to map out the attack surface and find potential vulnerabilities to exploit.

8. How does Wireshark complement port scanning?
Answer: While Nmap tells you which ports are open, running Wireshark allows you to see the exact packets (SYN, SYN/ACK, RST) being exchanged, helping you analyze the network traffic behavior in depth.
