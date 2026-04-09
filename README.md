# CyberSecurity-Task-1
# Task 1: Scan Local Network for Open Ports

## Objective
Learn to discover open ports on devices in a local network to understand network exposure.

## Tools Used
* Nmap (Network Mapper)
* Kali/Ubuntu Linux Terminal (VMware)

## Step-by-Step Process
1. I checked my virtual machine's local IP network range using the `ip a` command. My network range was `192.168.52.0/24`.
2. I ran a TCP SYN scan using Nmap with root privileges. I used the `-Pn` flag to ensure devices blocking ping requests were still scanned.
   **Command used:** `sudo nmap -sS -Pn -oN scan_results.txt 192.168.52.128/24`
3. I outputted the results to a text file for review.

## Scan Results Analysis
The scan identified my VMware virtual network infrastructure:
* **Host 192.168.52.1:** Found Port 3306 (MySQL) open. **Security Risk:** Vulnerable to brute-force attacks or SQL exploitation if the database is outdated.
* **Host 192.168.52.2:** Found Port 53 (DNS) open. **Security Risk:** Susceptible to DNS spoofing if misconfigured.

## Interview Questions & Answers

1. **What is an open port?** An open port is a virtual entry point on a device where a specific network service or application is actively listening for incoming connections.
2. **How does Nmap perform a TCP SYN scan?** It sends a SYN packet. If the port responds with SYN-ACK (meaning it's open), Nmap immediately sends an RST (reset) packet to close the connection before it's fully established, making it a "half-open" scan.
3. **What risks are associated with open ports?** Open ports expose network services to the outside world. Attackers can exploit outdated software or weak passwords on these ports to gain unauthorized access.
4. **Explain the difference between TCP and UDP scanning.** TCP relies on a reliable 3-way handshake, making scanning accurate. UDP is connectionless, so scanning it is slower and less reliable because open UDP ports often do not send back a response.
5. **How can open ports be secured?** By closing unused ports, using firewalls to block unauthorized IP addresses, updating software, and using strong passwords.
6. **What is a firewall's role regarding ports?** It acts as a traffic cop, monitoring incoming/outgoing traffic and blocking or allowing data through specific ports based on security rules.
7. **What is a port scan and why do attackers perform it?** It is a technique to map out open ports on a network. Attackers use it during reconnaissance to find potential entry points and vulnerabilities to exploit.
8. **How does Wireshark complement port scanning?** Nmap provides a high-level summary of open ports, while Wireshark captures the actual raw packets on the network, allowing analysts to see the exact data exchange happening during the scan.
