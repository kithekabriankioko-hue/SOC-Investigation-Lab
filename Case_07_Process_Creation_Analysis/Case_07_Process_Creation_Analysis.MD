# Case 7: Process Creation Analysis (Suspicious Execution Chain)

## Objective
To analyze a simulated process execution scenario where a trusted application may be abused to execute malicious commands, potentially indicating malware delivery or script-based attack behavior.

## Data Source
- Simulated SOC scenario (no direct log source available)
- Focus: Process execution chain behavior analysis

## Scenario Description
A Microsoft Word document (winword.exe) is observed spawning PowerShell (powershell.exe), which is unusual normal user activity. The PowerShell process is then seen executing encoded or obfuscated commands.

## Detection Logic (Conceptual)
Suspicious indicators include:
- winword.exe spawning powershell.exe
- PowerShell executing encoded commands (-enc / -EncodedCommand)
- Unusual process execution chain not typical for user behavior

## Analysis
This behavior is suspicious because Microsoft Word should not normally execute PowerShell processes. The presence of encoded or obfuscated commands suggests possible malicious intent, such as:

- Macro-based malware execution
- Script obfuscation to bypass security processes
- payload delivery
- Potential command execution by attacker

This type of behavior is commonly associated with phishing-based attacks where malicious documents are used as an entry point.

## Actions 
- Validate parent-child process relationships
- Investigate user activity leading to document execution
- Check for similar process execution patterns across endpoints
- Isolate affected host if observed in real environment
- Escalate to Tier 2 with findings

## Conclusion
The observed process execution chain (winword.exe spawning powershell.exe with encoded commands) is highly suspicious and may indicate a macro-based malware execution attempt. Further investigation is required to confirm malicious activity.