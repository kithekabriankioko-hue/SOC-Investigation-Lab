
# Scenario Overview

I installed Sysmon on my Windows machine to understand what really happens in the background beyond normal Windows logs. I wanted to practice how a SOC analyst would actually detect something suspicious.


# Objective

Learn how Sysmon logs work

Monitor process activity

Try to spot anything unusual


# Setup

Windows 10 machine

Sysmon installed

Logs viewed in Event Viewer


Path used: Event Viewer - Applications and Services Logs - Microsoft - Windows - Sysmon


# What I Saw

I focused mainly on Event ID 1 (Process Creation).

While checking logs, I noticed a PowerShell command that looked strange.

It had:

-nop

-w hidden

-enc



# Why It Looked Suspicious

From what I’ve learned:

-nop means no profile (avoids normal setup)

-w hidden hides the window

-enc means the command is encoded


This combination is not common for normal usage.


# My Thinking

I asked myself:  “Is this something a normal user would run?”

My answer: probably not.

So I treated it as suspicious.

It looks like something that could be:

a script being run silently

or someone trying to hide what they’re doing



# What I Checked

Looked at the full command

Checked the process details

Tried to understand where it came from



# If This Was Real

If this happened in a real SOC:

I would isolate the machine

Investigate the PowerShell command

Check for other related activity


# What I Learned

Sysmon gives better visibility than normal logs

PowerShell can be used in a suspicious way

Not everything malicious is obvious

# Evidence

![Sysmon Event](sysmon-event.png)

# Reflection

This helped me understand that being a SOC analyst is not just about tools.

It’s about asking:  “Does this look normal?”

That question alone helps a lot in investigations.