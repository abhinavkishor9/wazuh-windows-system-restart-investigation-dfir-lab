# wazuh-windows-system-restart-investigation-dfir-lab
## Overview

This Digital Forensics and Incident Response (DFIR) lab demonstrates how Windows system restart activity can be investigated using native Windows System logs and Wazuh.

Unlike Sysmon-based investigations, this lab relies entirely on Windows System Event Logs, Event Viewer, PowerShell, and Wazuh Discover to reconstruct restart activity and validate operating system startup and shutdown events.

The investigation also includes troubleshooting scenarios where expected restart Event IDs are not immediately visible, demonstrating how analysts validate Windows logging before drawing conclusions.

---

# Executive Summary

This investigation focused on reconstructing a Windows system restart using native Windows logging and Wazuh.

The investigation included:

- Performing a normal Windows restart
- Investigating restart-related System Event IDs
- Validating events using PowerShell
- Searching for restart events in Wazuh Discover
- Troubleshooting missing Event IDs
- Understanding differences in Windows event generation across builds

The investigation emphasizes structured DFIR methodology by validating Windows logs before relying on SIEM results.

---

# Learning Objectives

- Understand Windows restart-related Event IDs.
- Investigate Windows startup and shutdown activity.
- Validate System logs using Event Viewer.
- Verify restart events using PowerShell.
- Investigate restart activity in Wazuh Discover.
- Troubleshoot missing Windows events.
- Reconstruct a restart timeline.

---

# Skills Demonstrated

- Windows DFIR Investigation
- Windows System Log Analysis
- Startup & Shutdown Investigation
- Event Viewer Analysis
- PowerShell Event Validation
- Wazuh Discover Investigation
- Windows Event Correlation
- Timeline Reconstruction
- Digital Evidence Documentation
- DFIR Troubleshooting
- MITRE ATT&CK Mapping

---

# Tools Used

- Wazuh Dashboard (Discover)
- Windows Event Viewer
- Windows PowerShell
- Windows System Event Log
- Wazuh Agent

---

# Lab Environment

| Component | Details |
|-----------|---------|
| SIEM | Wazuh 4.12 |
| Endpoint | Windows 11 Pro |
| Server | Oracle Linux 9 |
| Investigation Type | Windows DFIR |
| Event Source | Windows System Log |
| Sysmon | Not Used |

---

# Investigation Scenario

A Windows workstation was restarted.

As the DFIR analyst, the objectives were to determine:

- When the restart occurred
- Which Windows events were generated
- Whether the restart was normal or unexpected
- Whether Wazuh collected the restart events
- Why expected Event IDs might not appear during investigation

---

# Investigation Workflow

1. Verify Wazuh agent connectivity.
2. Perform a normal Windows restart.
3. Examine Windows System logs.
4. Search restart Event IDs.
5. Validate events using PowerShell.
6. Investigate restart activity using Wazuh Discover.
7. Troubleshoot missing Event IDs.
8. Correlate investigative findings.
9. Document evidence.

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Defense Evasion | Indicator Removal on Host (Contextual restart investigation) | T1070 |
| Discovery | System Information Discovery | T1082 |

### Why Restart Investigations Matter

Unexpected or unexplained system restarts may indicate administrative maintenance, Windows Updates, malware activity, crashes, or attempts to disrupt forensic evidence. Correlating restart-related events helps analysts reconstruct endpoint activity during incident response.

---

# Evidence Collected

- Windows System Event Log
- Restart Event IDs
- Event Viewer
- PowerShell validation
- Wazuh Discover searches

---

# Evidence Correlation

| Evidence Source | Information Obtained | Investigation Value |
|-----------------|---------------------|--------------------|
| Event Viewer | Restart events | Primary evidence |
| PowerShell | Event validation | Independent verification |
| Wazuh Discover | Collected events | SIEM validation |

---

# Investigation Findings

- A normal Windows restart was performed.
- Windows System logs were examined.
- Initial PowerShell queries did not return the expected restart Event IDs.
- Additional troubleshooting was performed to determine whether the Windows build generated different restart events.
- The investigation highlighted the importance of validating Windows logging before assuming a SIEM collection issue.

---

# Key Takeaways

- Windows restart events vary between Windows versions.
- Event Viewer and PowerShell should always be used together.
- Missing Event IDs do not necessarily indicate logging failure.
- Wazuh investigations should always begin with validating Windows event generation.
- Multiple evidence sources improve investigation reliability.

---

