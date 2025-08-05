

##  Overview

This report summarizes the correlation of known threat intelligence Indicators of Compromise (IOCs) against endpoint activity logs using Splunk and Sysmon.

---

##  Objective

Detect any interaction between internal hosts and known malicious infrastructure based on external threat intelligence feeds.

---

##  Threat Intelligence Source

- **File:** threat_intel.csv
- **Sources:** AlienVault OTX
- **IOCs Included:**
  - Malicious IPs
  - Phishing domains
  - Test malware URLs

---

##  Methodology

1. **IOC Feed Ingested** into Splunk as a CSV Lookup Table
2. **Sysmon Logs Queried** for process executions and network connections
3. **Lookups Performed** using Splunk’s lookup command
4. **IOC Matches** isolated and visualized
5. **Alerts Created** for real-time detection of matches

---

##  Detection Summary

| IOC                   | Type       | Log Source | Match Found | Action |
|------------------------|------------|-------------|--------------|--------|
| 203.0.113.44           | IP Address | EventCode=3 |  Yes         | Blocked |
| secure-paypal-update.com | Domain     | EventCode=1 |  Yes         | Alert Triggered |
| eicar.com              | URL        | EventCode=1 |  Yes         | Logged |

---

##  Alert Configurations

- **Name:** IOC Match Detected
- **Trigger:** Result count > 0
- **Schedule:** Every 5 minutes
- **Action:** Log event (can be extended to email)

---

##  Dashboard Created

Panels included:
- Top IOCs Detected
- IOC Matches by Host
- IOC Type Breakdown (IP, Domain, URL)

---

##  Recommendations

- Integrate regular IOC feed updates using scheduled scripts
- Expand lookup fields to include hash values (MD5, SHA256)
- Enrich logs with GeoIP and WHOIS for deeper context
- Add suppression logic to reduce alert noise

---


