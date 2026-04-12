# Case 6: Brute Force Escalation Analysis (Threshold-Based Detection)

## Objective
To detect high-risk authentication activity using threshold-based analysis of failed login attempts and successful authentication events, which may indicate brute force attacks with higher severity conditions.

## Data Source
- sourcetype: Windows_test_logs  
- EventCode: 4625 (Failed Login)  
- EventCode: 4624 (Successful Login)

## Detection Query

index=main sourcetype="Windows_test_logs"
| stats count(eval(EventCode=4625)) as FailedLogins,
        count(eval(EventCode=4624)) as SuccessfulLogins
        by user, src_ip
| where FailedLogins > 10 OR (FailedLogins > 5 AND SuccessfulLogins > 0)

## Detection Result
The query identified authentication activity with elevated failed login attempts and successful logins following multiple failures. This indicates potentially high-risk authentication behavior requiring closer inspection.
 Screenshot: /screenshots/case6_result.png

## Analysis
This behavior is suspicious because a higher number of failed login attempts may indicate a brute force or password guessing attack. The presence of a successful login after repeated failures increases the likelihood of potential account compromise. The threshold-based detection helps identify more severe authentication patterns compared to normal login activity noise.

## Actions Taken
-Applied filtering to identify high-risk authentication events
-Analyzed failed vs successful login correlation per user and source IP
-Identified accounts exceeding abnormal login attempt thresholds
-Flagged suspicious authentication patterns for escalation review

## Conclusion
The observed authentication behavior may indicate a potential brute force attack with increased severity due to high failed login volume and successful authentication occurrence. Further investigation is recommended.