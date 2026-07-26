# Investigation Timeline

| Time | Activity | Evidence |
|------|----------|----------|
| 09:00 | Verified Wazuh agent connectivity | agent_control |
| 09:05 | Performed Windows restart | Windows |
| 09:10 | Reviewed Event Viewer | System Log |
| 09:15 | Queried restart Event IDs | PowerShell |
| 09:18 | Initial query returned no results | PowerShell |
| 09:22 | Began troubleshooting | Event Analysis |
| 09:28 | Investigated Wazuh Discover | Discover |
| 09:35 | Correlated findings | Documentation |

---

# Investigation Flow

Investigation Started

↓

Verified Agent Health

↓

Performed Windows Restart

↓

Reviewed Event Viewer

↓

Validated Using PowerShell

↓

Troubleshot Missing Event IDs

↓

Investigated Wazuh Discover

↓

Correlated Evidence

↓

Investigation Completed

---

# Summary

The investigation reconstructed Windows restart activity using native Windows System logs and Wazuh Discover. The lab emphasized validating Windows event generation, troubleshooting missing Event IDs, and correlating multiple evidence sources to produce a structured DFIR investigation.
