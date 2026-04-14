# SOC Investigation Lab

## Overview

This repository contains my SOC practice work based on simulated and test lab environments.

The goal is to understand how SOC analysts investigate security incidents using logs, SIEM queries, and endpoint logs.

Some cases use simulated log data (due to VM and environment limitations), while others include screenshots and query outputs from Splunk and Sysmon.

Each investigation focuses on identifying suspicious behaviour, understanding attack patterns, and writing structured incident analysis.


## Investigation Structure

Each case follows a general SOC workflow:

- log review and filtering  
- identifying suspicious patterns  
- correlating events (users, IPs, processes)  
- mapping behaviour to possible attack types  
- documenting findings  

## Cases

### Case 01 — Brute Force Attack

- analysed Windows Event ID 4625 (failed logins)  
- identified repeated authentication failures  
- reviewed source IP behaviour  
- detected possible brute force / password guessing attempts  

*Notes:* Includes logs, screenshots, Splunk queries, and report analysis.

### Case 02 — Suspicious Authentication Activity

- analysed Event ID 4624 and 4625  
- correlated multiple user login attempts  
- identified low-attempt patterns across users  
- used Splunk queries for detection  

*Notes:* Includes logs, screenshots, Splunk queries, and report analysis.

### Case 03 — Sysmon Analysis

- analysed Sysmon Event ID 1 (process creation)  
- analysed Sysmon Event ID 3 (network connections)  
- reviewed process behaviour and execution chains  
- identified suspicious endpoint activity patterns  

### Case 04 — Suspicious PowerShell Activity

- analysed PowerShell execution behaviour  
- identified encoded command usage  
- reviewed parent-child process relationships  
- checked for external IP connections  

*Notes:* This case file is based on a simulated scenario I created during my SOC Hands-on training due to environment limitations.


### Case 05 — Lateral Movement Investigation

- analysed authentication across multiple systems  
- reviewed repeated access attempts  
- correlated user and IP activity  
- identified possible movement between systems  

*Notes:* Screenshot-based analysis and written investigation report.


### Case 06 — Brute Force Escalation Analysis

- analysed repeated failed login attempts  
- checked for successful authentication after failures  
- correlated timeline of user activity  
- reviewed escalation patterns from brute force attempts  

*Notes:* Report-based analysis supported by logs.

### Case 07 — Process Creation Analysis

- analyzed process execution behaviour  
- reviewed parent-child process relationships  
- identified unusual execution chains  
- correlated process activity patterns  

*Notes:* Report-based SOC analysis of process behaviour.

## Tools Used

- Splunk (SIEM)  
- Sysmon (Endpoint Monitoring)  
- Windows Event Logs  
- Test Log Environment (Windows_test_logs)  

## Skills Demonstrated

- Security log analysis  
- Threat detection and investigation  
- SOC alert triage  
- Attack pattern recognition  
- Endpoint monitoring and process analysis  
- SIEM querying (Splunk SPL)  
- Incident reporting and documentation  

