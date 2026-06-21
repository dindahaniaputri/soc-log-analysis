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


![Uploading Screenshot 2026-06-21 134211.png…]()



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






















































































































































































