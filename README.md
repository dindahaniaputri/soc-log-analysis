# Web Log Analysis using Splunk

## Objective
This project aims to analyze web logs using Splunk to detect suspicious activity.

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
<img width="1920" height="908" alt="time chart" src="https://github.com/user-attachments/assets/46a8cf91-09b3-4415-a01a-487441212a74" />

## User-Agent Analysis
<img width="1920" height="910" alt="useragent" src="https://github.com/user-attachments/assets/1a30171a-2c14-4368-a202-95fa39cba0dd" />

## Findings
- IP 208.91.156.11 generated many requests
- Targeted a non-existent file
- All responses returned 404
- User-agent identified as "Chef Client"

## Analysis
The repeated requests to a non-existent file indicate abnormal behavior.

The use of "Chef Client" suggests automated activity rather than a human user.

This pattern is consistent with scanning or probing attempts.

## Conclusion
The activity is classified as suspicious due to repeated failed requests and automated behavior.

## Recommendation
- Monitor the IP for further activity
- Investigate similar patterns
- Consider blocking if confirmed malicious
