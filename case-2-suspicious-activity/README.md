# Case 02 – Distributed Brute Force Attack

## Description
This case demonstrates the detection and analysis of a distributed brute force attack using Windows authentication logs in Splunk.

## Key Skills Demonstrated
- Log analysis using Splunk
- Detection of brute force attacks
- Correlation of failed and successful logins
- Time-based attack analysis
- Identification of compromised accounts

## Tools Used
- Splunk
- Windows Event Logs

## Summary
-I noticed multiple IP addresses (192.168.1.10, 10.0.0.5, 192.168.1.20)repeatedly attempting logins against the same accounts.The user test stood out as the most targeted account across all three IPs.
-When I broke the logs down by time, I could clearly see a spike in failed logins within a specific hour.