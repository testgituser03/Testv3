# Assignment Submission: Lab Experiment 3  
## System and Web Server Fingerprinting  

**Submitted by**: [Your Full Name]  
**Course**: [Course Name/Code]  
**Instructor**: [Instructor's Name]  
**Submission Date**: February 20, 2025  

---

## Objective  
The purpose of this lab experiment is to perform system fingerprinting using various tools to gather detailed information about a web server, including its operating system, open ports, services, and web technologies.

## Tools Used  
The following tools were utilized to complete the fingerprinting tasks:  
1. **Nmap** - Network exploration and security auditing tool.  
2. **Netcat** - Versatile networking utility for reading/writing data across network connections.  
3. **WhatWeb** - Web scanner for identifying technologies used by websites.  
4. **Wappalyzer** - Browser extension for analyzing web application technologies.

## Experimental Procedure  

### Step 1: Fingerprinting the Web Server using Nmap  
Nmap was employed to scan an Ubuntu virtual machine and a Windows-based server to identify open ports, running services, and the underlying operating system. The results were captured and analyzed.

#### 1.1 Ubuntu VM Nmap Scan  
- **Command**: `sudo nmap -O 192.168.157.129`  
- **Results**:  
  - Host status: Up (latency: 0.0020s).  
  - Open ports:  
    - 80/tcp (HTTP)  
    - 443/tcp (HTTPS)  
  - Detected OS: Linux Kernel 4.x - 5.x  
  - MAC Address: 00:0C:29:A5:1A:52 (VMware)  
  - Note: OS detection provided possible matches but was not fully conclusive.

#### 1.2 Windows Server Nmap Scan  
- **Command**: `sudo nmap -O 10.1.180.47`  
- **Results**:  
  - Host status: Up (latency: 0.0029s).  
  - Open ports:  
    - 135/tcp (Microsoft RPC)  
    - 139/tcp (NetBIOS Session Service)  
    - 445/tcp (Microsoft-DS)  
    - 903/tcp (ISS Console Manager)  
    - 3389/tcp (RDP - Remote Desktop Protocol)  
    - 7070/tcp (RealServer)  
    - 8080/tcp (HTTP Proxy)  
  - OS Detection:  
    - Likely matches: Windows XP SP3, Windows 7, Windows Server 2012 (93% certainty)  
    - Other possibilities: VMware NAT Device, Linux 3.2/4.4  
  - Note: OS detection was inconclusive due to test conditions.

#### 1.3 Packet Capture Process  
- **Command**: `dumpcap -i 1 -w os-fingerprint-file-S.pcapng`  
- **Details**:  
  - Network packets were captured during the Nmap scan and saved in `.pcapng` format.  
  - Analysis of captured packets provided insights into network responses and interactions between the scanning system and the target.

---

### Step 2: Fingerprinting the System using Netcat  

#### 2.1 Sending an HTTP Request and Grabbing the HTTP Server Banner  
- **Procedure**:  
  - A manual HTTP request was sent to the web server using Netcat.  
  - The response included details such as HTTP version, server type, and additional headers.  
- **Finding**: The server was identified as running Apache on an Ubuntu system.

#### 2.2 Remote Access Shell using Netcat  
- **Attacker Side**:  
  - Initiated a connection with the target system.  
  - Retrieved the attacker’s public IP address for verification.  
  - Identified network devices within the subnet.  
- **Victim Side**:  
  - Exploited the target machine using a reverse shell technique.  
  - Successfully executed remote commands on the victim’s system.

#### 2.3 File Transfer / Simple Chat using Netcat  
- **Sender Process**:  
  - Transmitted data to the target system.  
  - Verified successful transmission by checking the received file.  
- **Receiver Process**:  
  - Set up a Netcat listener to capture incoming data.  
  - Saved received data into `received.txt` for further analysis.

---

### Step 3: Fingerprinting the System using WhatWeb  

#### 3.1 WhatWeb Scan on SRM Website  
- **Command**: `whatweb -v srmap.edu.in`  
- **Results**:  
  - Detected technologies:  
    - CMS: WordPress  
    - Server: Apache  
    - Security Headers: CSP, X-Frame-Options  
    - JavaScript Frameworks: jQuery  
    - Hosting Provider Information  
  - Observations:  
    - The website uses WordPress as its CMS with multiple security headers for protection.  
    - Results saved in `srmap_edu.txt`.

---

### Step 4: Fingerprinting the System using Wappalyzer  

#### 4.1 Wappalyzer Analysis of SRM Website  
- **Method**: Analyzed `srmap.edu.in` using the Wappalyzer browser extension.  
- **Detected Technologies**:  
  - CMS: WordPress 6.4.5  
  - Databases: MySQL  
  - Analytics: Google Analytics, Facebook Pixel, LinkedIn Insight Tag  
  - Advertising: Microsoft Advertising  
  - SEO Tools: Yoast SEO Premium  
  - Security Features: SSL/TLS Encryption  
- **Observations**:  
  - The site leverages third-party services for analytics, advertising, and SEO optimization.  
  - Results exported to `wappalyzer_srmap-edu.in.csv` for further analysis.

---

## Conclusion  
This experiment demonstrated the effectiveness of multiple tools in fingerprinting web servers and systems:  
- **Nmap and Netcat**: Delivered a detailed fingerprint of target systems, identifying services and security posture.  
- **Packet Capture**: Enhanced understanding of network interactions.  
- **WhatWeb and Wappalyzer**: Provided insights into web technologies, security features, and third-party integrations.  

Collectively, these techniques form a robust approach to assessing a target’s security posture and identifying potential vulnerabilities, offering valuable data for network security analysis.

---
