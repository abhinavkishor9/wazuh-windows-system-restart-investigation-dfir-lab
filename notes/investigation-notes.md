# Investigation Notes

## Lab Summary

This investigation focused on analyzing Windows system restart activity using native Windows System logs and Wazuh Discover.

The investigation reconstructed restart activity by correlating Event Viewer, PowerShell, and Wazuh while troubleshooting missing restart Event IDs.

---

## Analyst Methodology

The investigation followed a structured DFIR workflow:

1. Verify Wazuh agent connectivity.
2. Perform a Windows restart.
3. Examine Windows System logs.
4. Search restart-related Event IDs.
5. Validate events using PowerShell.
6. Search Wazuh Discover.
7. Troubleshoot missing events.
8. Correlate evidence.
9. Document findings.

---

## Investigation Scenario

A Windows workstation was restarted.

The investigation aimed to determine:

- Whether restart events were generated.
- Which Event IDs were present.
- Whether Wazuh successfully collected restart activity.
- Why expected Event IDs were initially unavailable.

---

## Evidence Collected

### Evidence 1 – Windows Restart

Collected:

- Restart operation

Finding:

Established investigation baseline.

---

### Evidence 2 – Event Viewer

Collected:

- Windows System events
- Restart-related Event IDs

Finding:

Used as the primary source for restart investigation.

---

### Evidence 3 – PowerShell Validation

Command Used

```powershell
Get-WinEvent -LogName System -MaxEvents 30 |
Where-Object {$_.Id -in 1074,6005,6006,6008,41,12,13}
```

Finding:

The initial query returned no results, prompting additional troubleshooting.

---

### Evidence 4 – Wazuh Discover

Collected:

- System log searches

Finding:

Used to validate restart-related event collection.

---

## DFIR Analysis

The investigation demonstrated that restart investigations should begin by validating Windows event generation before assuming SIEM collection issues.

Additional troubleshooting confirmed that different Windows builds may generate different restart-related events.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Defense Evasion | Indicator Removal on Host (Contextual) | T1070 |
| Discovery | System Information Discovery | T1082 |

---

## Analyst Observations

- Restart investigations require multiple evidence sources.
- Event Viewer remains the authoritative Windows source.
- PowerShell is useful for rapid validation.
- Missing Event IDs should be investigated before assuming collection failures.
- Windows versions may generate different restart-related events.

---

## Conclusion

The investigation demonstrated how Windows restart activity can be investigated using native Windows logging and Wazuh Discover while emphasizing structured troubleshooting when expected forensic artifacts are not immediately available.
