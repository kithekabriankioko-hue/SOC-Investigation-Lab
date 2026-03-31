[02:09, 24/03/2026] kitheka: # Identify failed and successful logons
index=main sourcetype="windows_test_logs" (EventCode=4625 OR EventCode=4624)
| stats count by EventCode

# Count per Source IP
index=main sourcetype="windows_test_logs" (EventCode=4625 OR EventCode=4624)
| stats count by src_ip, EventCode

# Investigate suspicious IP
index=main sourcetype="windows_test_logs" src_ip="192.168.1.20"
| stats count by user, EventCode

# Show full table of events
index=main sourcetype="windows_test_logs" src_ip="192.168.1.20"
| table _time, user, EventCode, src_ip, host
[02:11, 24/03/2026] kitheka: # Brute Force / Dictionary Attack on Domain Admin Account

## Objective
Analyze authentication logs in Splunk to identify suspicious login patterns.

## Data Source
- Log Type: windows_test_logs
- Platform: Splunk
- Fields Used: EventCode, user, src_ip, Hostname, _time

## Key Event Codes
- 4625 → Failed logon
- 4624 → Successful logon

## Methodology
1. Identify failed vs successful logons
2. Analyze activity by source IP
3. Investigate suspicious IP

## Findings
- Total Failed Logons (4625): 423
- Total Successful Logons (4624): 12
- Suspicious Source: 10.0.0.5
  - Failed: 147
  - Successful: 7
- Target: Domain Admin account

## Analysis
- Single source IP attempting multiple logins
- Repeated failures with eventual success
- Pattern consistent with brute-force / dictionary attack

## Conclusion
Potential compromise of admin account. Attack originates from 10.0.0.5.

## Recommendations
- Implement account lockout policies
- Monitor high failed login thresholds
- Investigate suspicious hosts
- Enforce MFA on privileged accounts