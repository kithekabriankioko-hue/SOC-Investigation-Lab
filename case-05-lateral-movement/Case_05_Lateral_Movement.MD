# Case 5: Authentication Anomaly (Possible Lateral Movement)

## Objective
To investigate suspicious authentication activity where a single user account is observed logging in from multiple source IP addresses using Windows_test_logs.

## Data Source
- sourcetype: Windows_test_logs  
- EventCode: 4624 (Successful Login)

## Detection Query

index=main sourcetype="Windows_test_logs" EventCode=4624
| stats dc(src_ip) as UniqueIPs, values(src_ip) as IPs by user
| where UniqueIPs > 1

## Detection Result
The query identified users with multiple source IP addresses associated with successful login events. This indicates unusual authentication behavior that may require further investigation.
Screenshot: /screenshots/case05_results.png

## Analysis
This activity may indicate possible credential sharing, account compromise, or lateral movement attempts. A single user account being accessed from multiple source IP addresses is not typical in normal user behavior and should be considered suspicious depending on the environment.

## Actions Taken
-Verified login patterns using splunk query
-Identified users with multiple source IPs 
-Correlated authentication behavior for anomalies
-Flagged suspicious accounts for  further investigation 

## Conclusion
The observed authentication pattern is suspicious and may indicate potential credential misuse or lateral movement activity. Further investigation is recommended to validate legitimacy of logins.
