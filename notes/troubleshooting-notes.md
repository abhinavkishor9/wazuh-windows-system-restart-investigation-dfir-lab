# Troubleshooting Notes

## Issue 1 — No Restart Events Returned

### Cause

The initial PowerShell query searched only the last 30 System events.

### Resolution

Increase the number of events or search by specific Event IDs using `FilterHashtable`.

---

## Issue 2 — Expected Event IDs Missing

### Cause

Different Windows builds may generate different restart-related events.

### Resolution

Enumerate recent System events to determine which restart events are produced on the endpoint.

---

## Issue 3 — No Results in Wazuh Discover

### Cause

Incorrect Event ID search or indexing delay.

### Resolution

Validate the event exists in Windows before investigating Wazuh.

---

## Issue 4 — Event Viewer and PowerShell Differ

### Cause

PowerShell query limitations or event filtering.

### Resolution

Verify directly in Event Viewer and adjust the PowerShell query accordingly.

---

## Issue 5 — Wazuh Agent Health

### Cause

Potential communication interruption.

### Resolution

Verify agent status using:

```bash
sudo /var/ossec/bin/agent_control -i 001
```

---

# Lessons Learned

- Always validate Windows logs before troubleshooting Wazuh.
- Restart-related Event IDs may differ across Windows versions.
- Event Viewer and PowerShell complement each other during DFIR investigations.
- Structured troubleshooting improves investigation accuracy.
