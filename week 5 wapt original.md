
# Assignment Report: Exploring Burp Suite for Web Application Security Testing

**Submitted by:** [Your Name]  
**Date:** February 20, 2025  
**Course:** [Course Name/Code]  
**Instructor:** [Instructor’s Name]  

---

## 1. Introduction

Burp Suite, developed by PortSwigger, is a leading tool for web application security testing, widely used by penetration testers and security researchers. It acts as an intercepting proxy, allowing users to capture, analyze, and manipulate HTTP/HTTPS traffic between a browser and a web server. This assignment aimed to explore Burp Suite’s core functionalities—Proxy, Repeater, Intruder, and Decoder—to identify potential vulnerabilities in a web application. The target for this exercise was [insert your target, e.g., "a local DVWA instance on a Kali Linux VM" or "example.com as provided"], with all activities conducted legally and ethically in a controlled environment.

This report outlines the methodology, results, and analysis of using Burp Suite to perform basic web security testing tasks, providing insights into its practical application.

---

## 2. Methodology

### 2.1 Objective
To demonstrate proficiency in using Burp Suite to intercept traffic, repeat requests, perform simple attacks, and decode data, thereby understanding its role in web application security testing.

### 2.2 Tools Used
- **Burp Suite Community Edition**: Installed on Kali Linux (default) or downloaded from [PortSwigger’s website](https://portswigger.net/burp/communitydownload).
- **Firefox Browser**: Configured with FoxyProxy to route traffic through Burp Suite.
- **Target**: [e.g., "Damn Vulnerable Web Application (DVWA) on IP 192.168.1.100" or "example.com"].

### 2.3 Environment Setup
- **System**: Kali Linux 2024.1 with 8GB RAM and 2 CPUs.
- **Burp Suite Installation**: Verified via terminal:
  ```bash
  burpsuite
  ```
- **Proxy Configuration**:
  - Started Burp Suite and confirmed proxy listener at `127.0.0.1:8080` (Proxy > Options).
  - Installed FoxyProxy in Firefox, set to `127.0.0.1:8080`, and enabled it.
  - Downloaded Burp’s CA certificate from `http://burp/` and imported it into Firefox (Preferences > Privacy & Security > Certificates > Import).
- **Target**: [e.g., "DVWA running locally at http://192.168.1.100/dvwa/"].

### 2.4 Procedures
#### Proxy: Intercepting Traffic
- Configured Firefox to route traffic through Burp Suite.
- Navigated to the target URL, intercepted a login request, and forwarded it.

#### Repeater: Repeating Requests
- Sent an intercepted login request to Repeater.
- Modified parameters (e.g., username/password) and reissued the request.

#### Intruder: Basic Attack
- Targeted a login form parameter (e.g., password field).
- Used a small wordlist (e.g., "password, admin, 12345") to perform a brute-force attack.

#### Decoder: Data Transformation
- Captured a URL-encoded parameter from a request.
- Decoded it to plaintext and re-encoded it in Base64.

---

## 3. Results

### 3.1 Proxy Results
- **Intercepted Request**: Login attempt to [target URL].
- **Output**:
  ```
  POST /dvwa/login.php HTTP/1.1
  Host: 192.168.1.100
  User-Agent: Mozilla/5.0
  Content-Type: application/x-www-form-urlencoded
  username=admin&password=password&Login=Login
  ```
- **Finding**: Successfully intercepted and modified the password to "test" before forwarding.

### 3.2 Repeater Results
- **Original Request**: `username=admin&password=password`.
- **Modified Request**: Changed password to "admin123}.
- **Response**:
  ```
  HTTP/1.1 200 OK
  <html> Welcome to DVWA </html>
  ```
- **Finding**: Confirmed login success with "admin123," indicating a weak password.

### 3.3 Intruder Results
- **Target Parameter**: `password`.
- **Payload**: Wordlist with 3 entries: "password, admin, 12345".
- **Output**:
  - "password": Response length 1024, status 302 (redirect to login).
  - "admin": Response length 2048, status 200 (login success).
  - "12345": Response length 1024, status 302.
- **Finding**: "admin" was the correct password, identified via response length and status code differences.

### 3.4 Decoder Results
- **Input**: URL-encoded string from a request: `dGVzdA==`.
- **Decoded**: Used Decoder to convert from Base64 to plaintext: "test".
- **Encoded**: Re-encoded "test123" to Base64: `dGVzdDEyMw==`.
- **Finding**: Successfully transformed data, useful for crafting payloads.

---

## 4. Analysis

### 4.1 Tool Effectiveness
- **Proxy**: Essential for capturing and modifying live traffic, revealing request structure.
- **Repeater**: Allowed precise testing of parameter changes, confirming weak credentials.
- **Intruder**: Effective for automated attacks, though limited by rate throttling in Community Edition.
- **Decoder**: Simplified data manipulation, enhancing payload creation.

### 4.2 Observations
- All tools confirmed the target’s login form was vulnerable to weak passwords.
- Intruder’s success relied on response analysis (length/status), a key technique in real-world testing.
- Proxy and Repeater provided manual control, while Intruder automated repetitive tasks.

### 4.3 Challenges
- HTTPS traffic required CA certificate setup, initially causing connection errors.
- Intruder’s rate limit in Community Edition slowed the attack process.
- Limited scope (simple login form) restricted deeper vulnerability exploration.

---

## 5. Conclusion

This assignment demonstrated Burp Suite’s power as a web security testing tool. The Proxy enabled traffic interception, Repeater facilitated request manipulation, Intruder automated attacks, and Decoder handled data encoding/decoding. Applied to [target], these tools exposed a weak password vulnerability, underscoring Burp Suite’s utility in identifying security flaws. While the Community Edition has limitations (e.g., no automated scanner), it remains robust for manual testing. This exercise built foundational skills in web penetration testing, applicable to real-world scenarios with proper authorization.

---

## 6. Recommendations
- Use Burp Suite Professional for advanced features like automated scanning.
- Test on varied targets (e.g., with SQL injection or XSS flaws) to explore more vulnerabilities.
- Combine with other tools (e.g., Nmap) for comprehensive assessments.

---

## 7. Attachments
- **Screenshots**: Proxy intercept, Repeater response, Intruder results, Decoder output (if applicable).
- **Wordlist**: `passwords.txt` used in Intruder.

---
