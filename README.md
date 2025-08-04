# Scan-Your-Local-Network-for-Open-Ports

# Overview
This project demonstrates basic network reconnaissance using Nmap and Wireshark to identify open ports, understand potential vulnerabilities, and assess local network exposure.

# Objectives
- Discover active hosts and open ports on the local network
- Identify running services and associated risks
- Capture and analyze packet traffic using Wireshark (GUI)
- Document findings in a structured report

# Tools Used
- **Nmap** (for port scanning)
- **Wireshark** (GUI-based packet capture and analysis)
- **Linux OS** (Kali/Debian based)

# Steps Performed

1. **Identified Local IP Range**
   - Used `ip a` to find the IP address and subnet.
   - Example: `192.168.1.0/24`

2. **Scanned Network with Nmap**
   - Command used:
     
     `nmap -sS 192.168.1.0/24 -oN scan_report.txt`
     
   - Performed a TCP SYN scan to identify open ports on live hosts.
   - Note: We could have used -sT for all tcp port scan but it will be visible as in -sS it don't follow through the entire handshake
           rather just wait to get ACK+SYC from the other end. While, using -sT it also respond to ACK+SYC with SYC flag , hence,
           making the entire connection. This can be later on can be detected by IDS or Firewall.

3. **Captured Traffic with Wireshark**
   - Opened Wireshark, selected the active interface.
   - Captured traffic while Nmap scan was running.
   - Filtered packets by protocols (e.g., TCP, DNS, HTTP). In our case we have used

     `tcp.flags.syn == 1 && tcp.flags.ack == 0`
     
4. **Analyzed Open Ports and Services**
   - For each discovered IP, noted open ports.
   - Researched known services and vulnerabilities.
   - Assessed potential security risks per port.

# Summary
The project provided hands-on experience with:
- Network mapping using Nmap
- Packet monitoring with Wireshark
- Identifying critical ports and associated vulnerabilities
- Writing clear documentation and analysis for future security audits
