# SOC Analysis Report: Case 02 – Suspicious Login Activity.

## Overview
This report focuses on detecting and analysing suspicious login attempts seen in Windows authentication logs using splunk. The goal was to identify potential brute force patterns and determine whether any Accounts were potentially compromised.
## Data Source
- Index: main  
- Sourcetype: windows_test_logs  
- Log Type:Windows Authentication Logs
## Investigation Notes
I ran correlation queries to see both failed and successful logins. The focus was on identifying patterns across multiple source IPs and users. The data showed that several IP addresses were attempting logins repeatedly, with some managing successful logins after many failures.
After that, I focused on specific users, ecspecially those receiving a high number og failed login attempts, to determine if they were bring targeted.
Finally, I analyzed login activity over time to identify attack spikes and understand when the attack was most active.
## Key Findings

- *User under investigation:* test  
- *Suspicious IPs:* 192.168.1.20, 10.0.0.5, 192.168.1.10  
- *Failed login counts:* 
  - 192.168.1.20 - 309  
  - 10.0.0.5 - 288  
  - 192.168.1.10 - 282  
- *Successful logins:* small numbers for each IP (5–7), indicating possible compromise  

-Across all IPs, the test account had the highest failed login numbers. This indicates that it was a key target
-Other IPs also showedhigh failed login counts with some successful attempts
-Time-based analysis showed a peak attack period where the number of failed logins was highest with a one-hour window.
## Analysis
-The activity observed shows a clear pattern of repeated login attempts across multiple accounts and IP addresses.
-The presence of a high number of failed logins followed by successful logins suggests that the attackers were attempting to guess passwords until successful authentication was achieved.
-The fact that multiple IP addresses were involved indicates that this was not a single-source attack but rather a distributedbrute force attack.
-High likelihood that the test account could be compromised as it shows the highest number of failed login attempts accross different IPs.   
-Attackers may have attempted access from multiple locations    
## Conclusion
-The investigation confirms a distributed brute force attack targeting multiple user accounts,with a strong focus on the 'test' account.
-The presence of successful logins after numerous failed attempts indicates a high likelihood of account compromise.
-The investigation shows a *coordinated login attack targeting a single high-risk user. While 192.168.1.20 generated the most failed login attempts, other IPs were also involved. 
## Recommendations
- Reset the password for the account test immediately  
- Review all activity tied to this account for unusual actions  
- Block and monitor suspicious IPs  
- Consider enabling multi-factor authentication (MFA)  
- Apply account lockout policies to prevent repeated brute-force attempts  
- Continue monitoring for similar activity across other accounts.