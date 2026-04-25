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
<img width="1920" height="1080" alt="Screenshot 2026-04-21 210703" src="https://github.com/user-attachments/assets/dab46d9c-0fdf-4679-ba5d-15c12460c402" />


## Suspicious IP Detection
<img width="1920" height="1080" alt="Screenshot 2026-04-21 211323" src="https://github.com/user-attachments/assets/70906391-4241-4326-99c9-e9606318b1eb" />


## Detailed Log Analysis
<img width="1920" height="1080" alt="Screenshot 2026-04-22 160743" src="https://github.com/user-attachments/assets/82975c28-0b33-4ca7-bac2-df2abc793a69" />


## User-Agent Analysis
<img width="1920" height="1080" alt="Screenshot 2026-04-22 162641" src="https://github.com/user-attachments/assets/12f72f3c-d856-46bf-a198-97330aa74f1e" />


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
