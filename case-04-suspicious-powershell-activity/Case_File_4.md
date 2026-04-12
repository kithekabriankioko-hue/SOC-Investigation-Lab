# Case File 4 - Suspicious PowerShell Activity and possible C2 communication

## Incident Summary
I found suspicious activity on one workstation where PowerShell was executed and after that the system started making repeated connections to an external IP address. The connections were happening every few minutes and this looked not normal.

From my understanding, this could be a possible malware infection or command and control communication.

## Data Sources
- Splunk SIEM
- Sysmon logs (Event ID 1 and Event ID 3)


## What I observed

### Process creation (Event ID 1)
- powershell.exe was executed on the system
- the command looked suspicious and could be encoded or hidden

### Network activity (Event ID 3)
- system was connecting to an external IP address
- connection was over HTTPS (port 443)
- connections were repeating every 10 minutes

## My analysis
From what I understand, this behaviour is not normal for PowerShell.

PowerShell is usually used for administration but here it looks like it is being used to communicate with an external server in a repeating pattern. This might be command and control (C2) communication used by malware.

## What I checked during investigation
- I checked the PowerShell command line for anything encoded or suspicious
- I checked the user account that executed the process
- I looked at the destination IP to see if it is known or suspicious
- I checked if there were similar processes running on the same system
- I also considered if other machines had similar activity

## Impact
If this is real malicious activity, it could mean:
- the system is infected with malware
- data could be sent outside the company
- attacker could move inside the network

## My response
- I would isolate the affected machine from the network
- I would escalate this to Tier 2 analyst for deeper investigation
- I would document my findings for reporting

## Conclusion
This activity looks highly suspicious based on my understanding. PowerShell execution followed by repeated external connections is not normal and could be malware communicating with a command and control server. I escalated it for further investigation.

## Note
This Case file is based on a simulated scenario I created during my SOC Hands-on training.It demonstrates how I would Investigate and respond to a real-world incident using Sysmon and SIEM concepts.