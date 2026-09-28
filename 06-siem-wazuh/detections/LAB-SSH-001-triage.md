# LAB-SSH-001 – Analyst Triage

## Case Status / Fallstatus

**Status:** Closed – Controlled Lab Simulation
**Disposition:** No confirmed compromise

---

## 1. Alert Summary / Alert-Zusammenfassung

Wazuh detected repeated SSH authentication attempts against the non-existent user `fakeuser` on SRV-01.

The activity triggered Wazuh Rule 5712 with Level 10 after multiple failed authentication attempts.

---

## 2. Environment / Umgebung

| Field / Feld | Value / Wert |
|---|---|
| SOC Manager | SOC-01 |
| SOC Manager IP | 192.168.220.129 |
| Target Host | SRV-01 |
| Target IP | 192.168.220.130 |
| Wazuh Agent | SRV-01 |
| Source IP | 192.168.220.129 |
| Username | fakeuser |

---

## 3. Detection / Erkennung

| Field / Feld | Value / Wert |
|---|---|
| Wazuh Rule | 5712 |
| Wazuh Level | 10 |
| Rule Description | SSH brute-force attempt using a non-existent user |
| MITRE ATT&CK | T1110 – Brute Force |
| Tactic | Credential Access |

---

## 4. Timeline / Ereignisablauf

| Time | Event / Ereignis |
|---|---|
| 11:14:42 | Non-existent user `fakeuser` login attempts detected |
| 11:14:47 | PAM authentication failure detected |
| 11:14:48 | PAM authentication failure detected |
| 11:14:49 | Additional `fakeuser` login attempt detected |
| 11:14:50 | Additional `fakeuser` login attempt detected |
| 11:14:55 | Additional `fakeuser` login attempt detected |
| 11:14:56 | Additional `fakeuser` login attempt detected |
| 11:15:02 | Additional `fakeuser` login attempt detected |
| 11:15:02 | Wazuh Rule 5712 triggered – Level 10 |

---

## 5. Investigation / Untersuchung


The Wazuh alert data was reviewed to determine whether the repeated authentication failures resulted in a successful authentication.

The investigation identified multiple failed authentication events associated with source IP `192.168.220.129` and username `fakeuser`.

No successful authentication event matching the investigated source was found in the reviewed Wazuh alerts.

---

## 6. Authentication Outcome / Authentifizierungsergebnis


The investigated activity resulted in repeated failed authentication attempts against a non-existent user.

No successful authentication was observed in the reviewed Wazuh alert data.


---

## 7. MITRE ATT&CK Mapping

**Technique:** T1110 – Brute Force
**Tactic:** Credential Access

The detection was mapped to MITRE ATT&CK technique T1110 because the activity involved repeated authentication attempts.

---

## 8. Analyst Assessment / Analystenbewertung



The activity is consistent with a brute-force authentication pattern.

However, the investigation did not identify evidence of successful authentication in the reviewed Wazuh alert data.

The activity was intentionally generated from SOC-01 as part of an authorized security monitoring laboratory simulation.

Based on the reviewed Wazuh alert data, no successful authentication or compromise was identified.

---

## 9. Response Decision / Reaktionsentscheidung



No containment action was required because the activity was intentionally generated as part of the laboratory simulation.

The detection was validated and the relevant evidence was preserved.

---

## 10. Lessons Learned / Erkenntnisse


- Validated end-to-end SSH log collection.
- Validated Wazuh event decoding and correlation.
- Validated Rule 5712 detection.
- Confirmed MITRE ATT&CK T1110 mapping.
- Demonstrated the difference between an alert and a confirmed compromise.
- Practiced evidence-based SOC alert triage.

---

## 11. Final Disposition / Abschlussbewertung

**Disposition:** Closed – Controlled Lab Simulation

**Detection Result:** Successful

**Successful Authentication:** Not observed in reviewed Wazuh alerts

**Confirmed Compromise in Reviewed Evidence:** No

**Containment Required:** No

**Evidence Preserved:** Yes
