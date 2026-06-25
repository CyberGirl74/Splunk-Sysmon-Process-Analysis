# Splunk Sysmon Process Analysis

## Overview

This project demonstrates how I used Splunk Enterprise and Microsoft Sysmon to investigate Windows process creation events (Sysmon Event ID 1). The objective was to gain hands-on experience using Splunk Search Processing Language (SPL) to identify process activity, analyze parent-child process relationships, and understand normal Windows behavior.

---

## Objectives

- Configure Splunk to ingest Sysmon logs
- Analyze Windows Event ID 1 (Process Creation)
- Practice writing SPL queries
- Investigate parent-child process relationships
- Identify frequently executed processes
- Develop hands-on blue team investigation skills

---

## Tools Used

- Splunk Enterprise 10.4
- Microsoft Sysmon
- Windows Event Logs
- Windows 11
- SPL (Search Processing Language)

---

## Sample SPL Queries

### Top Executed Processes

```spl
index=* EventCode=1
| top Image limit=10
```

### Most Common Parent Processes

```spl
index=* EventCode=1 Image="*powershell.exe"
| stats count by ParentImage
| sort -count
```

---

## Findings

During this investigation I observed:

- Frequent execution of Splunk background processes
- Parent-child relationships between Windows and Splunk processes
- Normal Windows command-line activity
- Process creation events captured by Sysmon Event ID 1
- PowerShell process execution originating from expected parent processes

---

## Security Note

Some screenshots and command-line outputs have intentionally been omitted from this public repository because they contain host-specific information, usernames, or operational details. This project demonstrates the investigation methodology while following responsible operational security (OPSEC) practices.

---

## Skills Demonstrated

- Splunk Search Processing Language (SPL)
- Windows Event Analysis
- Sysmon Log Investigation
- Process Creation Monitoring
- Parent Process Analysis
- Security Documentation
- Blue Team Fundamentals

---

## Future Improvements

- Investigate additional Sysmon Event IDs
- Build Splunk dashboards
- Create detection searches
- Develop custom alerts
- Expand into threat hunting scenarios
