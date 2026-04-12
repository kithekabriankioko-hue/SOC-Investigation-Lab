Case 01 — Brute Force / Dictionary Attack on Domain Account

# Scenario

While analyzing Windows authentication logs in Splunk, I identified abnormal login behavior targeting a domain account. The logs showed repeated failed login attempts followed by successful logins, indicating a possible brute force / dictionary attack.


# Objective

- Detect brute force or dictionary attack activity
- Analyze authentication patterns (failed vs successful logins)
- Identify source IP responsible for the activity
- Determine if a compromise occurred

# Investigation (Splunk Analysis)

I analyzed Windows test logs using Event IDs:

- 4625 - Failed login attempts
- 4624 - Successful login attempts

Overall log summary:

- Total failed logins (4625): 423
- Total successful logins (4624): 12

Source IP correlation:

- Suspicious IP: 10.0.0.5
  - Failed logins (4625): 147
  - Successful logins (4624): 7

Additional query analysis also showed:

- Large volume of authentication attempts from the same source IP
- Repeated failures followed by eventual successful authentication


# Findings

The activity shows a clear pattern of:

- Repeated login attempts from a single source
- High number of failed authentications
- Eventual successful logins from the same IP

This behavior is consistent with a brute force / dictionary attack targeting a domain account.


# Conclusion

A potential compromise was identified.

The attacker (10.0.0.5) successfully authenticated after multiple failed attempts, indicating that credentials may have been guessed or cracked.


# Recommendations

- Implement account lockout policies after multiple failed attempts
- Enforce Multi-Factor Authentication (MFA) on domain accounts
- Monitor high-frequency authentication failures in real time
- Investigate host 10.0.0.5 for malware or unauthorized access
- Set alerts for abnormal Event ID 4625 spikes

# Evidence

- Splunk query results (Event ID 4624 / 4625 analysis)
- Source IP breakdown
- Authentication failure/success correlation charts