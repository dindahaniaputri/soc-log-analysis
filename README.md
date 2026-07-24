# SOC Log Analysis using Splunk

## Objective
This project aims to analyze web logs using Splunk to detect suspicious activity.
This project simulates basic SOC investigation workflow.
## Tools
- Splunk
- Apache Logs

## Analysis Process
- Checked status codes to identify normal vs abnormal activity
- Identified IPs generating high number of 404 errors
- Investigated specific IP behavior
- Analyzed user-agent to determine if activity was automated


## Status Overview
<img width="1920" height="738" alt="by stats" src="https://github.com/user-attachments/assets/8acf9d3f-33fe-4476-979e-75b20c6a05a6" />



## Suspicious IP Detection
<img width="1920" height="910" alt="by clientip" src="https://github.com/user-attachments/assets/d50d6fc5-7932-43ea-96a5-a80be8b34340" />


## Detailed Log Analysis
<img width="1920" height="908" alt="time chart" src="https://github.com/user-attachments/assets/16ec7f8d-153d-4263-b45c-2503de7170f6" />

## User-Agent Analysis
<img width="1920" height="910" alt="useragent" src="https://github.com/user-attachments/assets/1a30171a-2c14-4368-a202-95fa39cba0dd" />

## Findings
- IP 208.91.156.11 generated many requests
- Targeted a non-existent file
- All responses returned 404
- User-agent identified as "Chef Client"
- - The activity was repeated in a short time frame

## Analysis
The repeated requests to a non-existent file indicate abnormal behavior.

The use of "Chef Client" suggests automated activity rather than a human user.

This pattern is consistent with scanning or probing attempts.
The behavior is not typical of normal users and indicates possible automated scanning activity.

## Conclusion
The activity is classified as suspicious due to repeated failed requests and automated behavior.
From a SOC analyst perspective, this activity would be classified as low to medium severity and should be monitored for further escalation.

## Recommendation
- Monitor the IP for further activity
- Investigate similar patterns
- Consider blocking if confirmed malicious








---

## Brute Force Attack Detection using Splunk

### Objective
This project aims to detect brute force attacks by analyzing authentication logs.

### Tools
- Splunk
- JSON Logs

### Analysis Process
- Extracted fields using spath
- Expanded password arrays using mvexpand
- Counted password attempts per username
- Identified common password patterns

### Screenshots

#### Username Target Analysis
<img width="1907" height="913" alt="Screenshot 2026-04-28 210155" src="https://github.com/user-attachments/assets/f301550b-c7df-4cd1-9bac-c14eb1ca71d1" />


#### Password Pattern Analysis
<img width="1916" height="909" alt="Screenshot 2026-04-28 210336" src="https://github.com/user-attachments/assets/aa29a896-6546-4c62-a9c5-7476e8877323" />



### Findings
- The "root" account received the highest number of login attempts (over 400,000 attempts)
- Other accounts such as "admin" and "ubuntu" were also targeted
- Common passwords such as "123456", "password", and "admin" were frequently used

### Analysis
This behavior indicates a dictionary-based brute force attack, where attackers use common passwords to gain access.

The "root" account is a high-privilege account, making it a primary target.

### Conclusion
The activity is classified as a high-risk brute force attack targeting privileged accounts.



# Network Traffic Analysis Using Wireshark

## Overview

This project demonstrates basic network traffic analysis using Wireshark. The objective is to identify common network protocols and understand how devices communicate during normal web browsing activities.

---

## Tools Used

- Wireshark
- Windows 11
- Wi-Fi Network

---

## DNS Analysis

<img width="1536" height="683" alt="Screenshot 2026-06-21 133557" src="https://github.com/user-attachments/assets/2526afec-9c7d-40fe-9817-4202a47a3011" />




### Findings

The DNS filter was used to capture domain name resolution traffic.

Observed domains:

- www.google.com
- optimizationguide-pa.googleapis.com

The system performed both IPv4 (A) and IPv6 (AAAA) lookups to resolve domain names into IP addresses.

### Security Analysis

DNS traffic can help SOC analysts identify:

- Suspicious domains
- Malware command-and-control communication
- Unauthorized external connections

During this analysis, no suspicious domain activity was detected.

---

## TCP Three-Way Handshake Analysis

<img width="1532" height="762" alt="Screenshot 2026-06-21 133824" src="https://github.com/user-attachments/assets/523c3e52-fc0e-4428-ab96-e2b833a5a96d" />


### Findings

TCP SYN packets were captured to observe connection establishment between the client and remote servers.

Observed process:

1. SYN
2. SYN-ACK
3. ACK

This sequence confirms a successful TCP three-way handshake.

### Security Analysis

SOC analysts use TCP handshake analysis to detect:

- Port scanning
- Connection anomalies
- SYN flood attacks
- Unauthorized network activity

No abnormal TCP behavior was observed during this capture.

---

## TLS Traffic Analysis


<img width="1512" height="760" alt="Screenshot 2026-06-21 134211" src="https://github.com/user-attachments/assets/c04e0f8a-c673-4c72-a05d-afecd9df4cd6" />




### Findings

Encrypted HTTPS traffic was identified using TLSv1.2 and QUIC protocols.

Observed:

- TLSv1.2 Application Data
- QUIC traffic
- Encrypted communications between the client and external servers

### Security Analysis

TLS traffic analysis helps SOC analysts:

- Identify encrypted communications
- Verify secure connections
- Investigate suspicious destination IP addresses
- Monitor external communications

The captured traffic appeared consistent with normal web browsing behavior.

---

## Conclusion

This project demonstrated the analysis of three important network communication components:

- DNS name resolution
- TCP connection establishment
- TLS encrypted communications

The captured traffic showed normal browsing activity with no evidence of suspicious behavior.

---

## Skills Demonstrated

- Network Traffic Analysis
- Wireshark
- DNS Analysis
- TCP Three-Way Handshake Analysis
- TLS Traffic Analysis
- Security Monitoring
- SOC Fundamentals





# Install Web Server and DVWA Setup

## Overview

This project demonstrates the deployment of a vulnerable web application environment for cybersecurity auditing and penetration testing.

The objective was to build a realistic target environment by installing Apache Web Server, PHP, MariaDB, and Damn Vulnerable Web Application (DVWA) on Ubuntu Server.

## Tools Used

- Ubuntu Server
- Apache2
- PHP
- MariaDB
- DVWA
- Kali Linux
- VirtualBox

## Environment

- Target Machine: Ubuntu Server
- Auditor Machine: Kali Linux
- Web Server: Apache2
- Database: MariaDB
- Application: DVWA

---

## 1. Apache Web Server Installation

### Objective

Install and configure Apache Web Server.

### Findings

- Apache installed successfully.
- Web service was accessible from the network.

### Security Analysis

A running web service provides the foundation for application deployment and security testing.

---

## 2. PHP Installation

### Objective

Install PHP for dynamic web application support.

### Findings

- PHP installed successfully.
- Apache processed PHP applications correctly.

### Security Analysis

Dynamic web applications process user input and may introduce security risks if not properly validated.

---

## 3. MariaDB Installation

### Objective

Deploy the database server.

### Findings

- MariaDB installed successfully.
- Database service was operational.

### Security Analysis

The database stores sensitive information and should be securely configured.

---

## 4. DVWA Installation

### Objective

Deploy the Damn Vulnerable Web Application.

### Findings

- DVWA installed successfully.
- Application database configured.
- Login page accessible.

### Security Analysis

DVWA provides a safe environment for learning web application security testing.

---

## Key Findings

- Apache Web Server successfully deployed.
- PHP configured correctly.
- MariaDB database operational.
- DVWA successfully installed.
- Web application accessible from Kali Linux.

---

## Skills Demonstrated

- Linux Administration
- Apache Web Server
- PHP Configuration
- MariaDB
- Web Application Deployment
- Security Lab Setup

---

## Screenshots

### Apache Service Status

<img width="900" height="563" alt="image" src="https://github.com/user-attachments/assets/6b4f89ac-7441-46b9-b159-059584af8dcf" />


### Apache Default Page

<img width="938" height="503" alt="image" src="https://github.com/user-attachments/assets/710e4cde-6edb-49be-b013-1ddbd1a7618d" />


### DVWA Installation

<img width="830" height="519" alt="image" src="https://github.com/user-attachments/assets/f572327b-d963-404a-b8d6-d3258f46dca4" />


### Database Configuration

<img width="880" height="550" alt="image" src="https://github.com/user-attachments/assets/5f78d113-2e22-4cd5-83af-f3e8690d1066" />


### DVWA Configuration

<img width="980" height="613" alt="image" src="https://github.com/user-attachments/assets/c7b1f900-eace-4c65-95ea-3c181313221e" />


### DVWA Login

<img width="961" height="518" alt="image" src="https://github.com/user-attachments/assets/a2c27fbe-3769-4f80-bc8b-5e284ada4640" />


---

## Conclusion

This project demonstrates the deployment of a vulnerable web application environment used for cybersecurity auditing, penetration testing, and web application security assessment.





# Network Service Discovery Using Nmap

## Overview

This project demonstrates network reconnaissance and service discovery using Nmap in a controlled cybersecurity audit laboratory environment.

The objective was to identify exposed services, discover running software, and evaluate information disclosure risks from a network perspective.

## Tools Used

- Nmap
- Kali Linux
- Ubuntu Server
- VirtualBox

## Environment

- Auditor Machine: Kali Linux
- Target Machine: Ubuntu Server
- Target Address: 10.0.2.2
- Exposed Service Port: 8080

---

## 1. Basic Port Scan

### Objective

Identify open ports exposed to the network.

### Command

```bash
nmap -p 8080 10.0.2.2
```

### Findings

- Port 8080/TCP was open.
- The service was accessible from the network.

### Security Analysis

Open ports increase the organization's attack surface.

---

## 2. Service Version Detection

### Command

```bash
nmap -sV -p 8080 10.0.2.2
```

### Findings

- Apache HTTP Server detected.
- Service version information exposed.

---

## 3. Operating System Detection

### Command

```bash
sudo nmap -O 10.0.2.2
```

### Findings

- Operating system successfully identified.

---

## 4. Aggressive Scan

### Command

```bash
sudo nmap -A -p 8080 10.0.2.2
```

### Findings

- Service version detected.
- Operating system detected.
- Information disclosure identified.

---

## Skills Demonstrated

- Network Reconnaissance
- Service Enumeration
- Port Scanning
- OS Detection
- Security Assessment

---

## Screenshots

### Basic Port Scan

<img width="801" height="565" alt="image" src="https://github.com/user-attachments/assets/a11d5fba-287f-4754-ab5c-31f26d048923" />


### Service Detection

<img width="845" height="663" alt="image" src="https://github.com/user-attachments/assets/5101b0eb-002b-4e6a-a7fc-2b60ad947c1f" />

### Operating System Detection


<img width="895" height="672" alt="image" src="https://github.com/user-attachments/assets/cf4b7da4-357c-4bc8-aa5a-97fc51a3cda0" />

### Aggressive Scan

<img width="843" height="680" alt="image" src="https://github.com/user-attachments/assets/9dc6d34a-ff91-4138-8746-38686c0b19c5" />
<img width="794" height="622" alt="image" src="https://github.com/user-attachments/assets/511fdba2-a4eb-46fa-b9d3-04ac8d766806" />



---

## Conclusion

This project demonstrates how Nmap can be used to perform reconnaissance and identify exposed services during a cybersecurity assessment.



# Web Application Vulnerability Testing Using DVWA

## Overview

This project demonstrates web application vulnerability testing using Damn Vulnerable Web Application (DVWA).

The objective was to identify common web vulnerabilities including Authentication Weaknesses, SQL Injection, and Cross-Site Scripting (XSS).

## Tools Used

- DVWA
- Kali Linux
- Ubuntu Server
- Apache
- MariaDB

---

## 1. Authentication Weakness Testing

### Findings

- Unlimited login attempts allowed.
- No account lockout implemented.

### Security Analysis

Weak authentication controls allow brute force attacks.

---

## 2. SQL Injection Testing

### Payload

```sql
1' OR '1'='1
```

### Findings

- Multiple user records returned.
- Input validation not implemented.

---

## 3. Cross-Site Scripting (XSS)

### Payload

```html
<script>alert('Hacked')</script>
```

### Findings

- JavaScript executed successfully.
- User input reflected without validation.

---

## Key Findings

- Authentication Weakness
- SQL Injection
- Cross-Site Scripting (XSS)

---

## Skills Demonstrated

- Web Security Testing
- SQL Injection
- XSS
- Authentication Testing
- Vulnerability Assessment

---

## Screenshots

### DVWA Login
<img width="888" height="978" alt="image" src="https://github.com/user-attachments/assets/fbfea60a-7378-4f00-9676-b4d3282cc9da" />


### Security Level
<img width="975" height="883" alt="image" src="https://github.com/user-attachments/assets/82d3d183-5534-4d2b-a645-2c025bb40e53" />



### Authentication Weakness

<img width="765" height="714" alt="image" src="https://github.com/user-attachments/assets/8f22b5bc-f004-4de8-8fc2-cbab1d078ff3" />


### SQL Injection

<img width="882" height="796" alt="image" src="https://github.com/user-attachments/assets/0ff64f1d-156c-4495-a5bf-83a858397b2e" />
<img width="888" height="803" alt="image" src="https://github.com/user-attachments/assets/7ce06d95-0555-4939-84f0-32ac198c9850" />



### XSS Testing

<img width="833" height="752" alt="image" src="https://github.com/user-attachments/assets/e40ea200-5145-4e20-95be-eee6e2b6f858" />


### XSS Popup

<img width="975" height="468" alt="image" src="https://github.com/user-attachments/assets/6aecacb5-2e4d-45c8-86ea-deaee744fe9b" />


---

## Conclusion

This project demonstrates the identification of common web application vulnerabilities and their impact on application security.




# Security Monitoring Audit Using Wazuh SIEM

## Overview

This project demonstrates security monitoring and incident detection using Wazuh SIEM in a controlled cybersecurity laboratory environment.

The objective was to evaluate security monitoring capabilities through simulated attack scenarios.

## Tools Used

- Wazuh SIEM
- Kali Linux
- Ubuntu Server
- DVWA
- VirtualBox

---

## 1. Wazuh Agent Verification

### Findings

- Agent connected successfully.
- Security logs transmitted correctly.

---

## 2. SSH Brute Force Detection

### Findings

- Multiple failed login attempts detected.
- Authentication alerts generated.

---

## 3. File Integrity Monitoring

### Findings

- File modifications detected.
- Integrity alerts generated.

---

## 4. SQL Injection Detection

### Findings

- SQL Injection activity detected.
- Web security alerts generated.

---

## Key Findings

- Authentication Monitoring
- File Integrity Monitoring
- Web Attack Detection
- SIEM Alerting

---

## Skills Demonstrated

- SIEM
- Security Monitoring
- Incident Detection
- Log Analysis
- Threat Detection

---

## Screenshots

### Wazuh Agent

<img width="975" height="691" alt="image" src="https://github.com/user-attachments/assets/99a42cf7-51bf-487c-8594-ac6416c26fa2" />

### Wazuh Dashboard

<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/22f39e8c-dbd3-4513-8488-2496256ac0f6" />


### Agent Summary

<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/f7b9cbc0-5c39-4099-a9bf-0ff703e7f70e" />


### SSH Brute Force Alert

<img width="975" height="835" alt="image" src="https://github.com/user-attachments/assets/a5a3235d-0a64-4f28-938c-15513ead49a1" />


### Authentication Logs

<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/5b111231-4bb5-45db-af59-42b315597c02" />
<img width="975" height="549" alt="image" src="https://github.com/user-attachments/assets/102e3374-075b-4ee5-a6fa-016ebe13a5ee" />


### File Integrity Monitoring

<img width="975" height="731" alt="image" src="https://github.com/user-attachments/assets/c189b5cf-fca6-43b3-9f66-d0952757c605" />


### SQL Injection Alert

<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/b74feabf-e285-4903-9822-d500ca0fdcb2" />


---

## Conclusion

This project demonstrates the use of Wazuh SIEM to monitor security events, detect attacks, and investigate incidents in a Linux environment.

































































































































































