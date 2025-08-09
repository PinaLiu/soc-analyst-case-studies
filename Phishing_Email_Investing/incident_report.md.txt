# Incident Report – Phishing Email Investigation

**Date of Investigation:** 2025-08-09  
**Analyst:** Giusi Liuzza  
**Incident Type:** Phishing Email with Malicious Attachment  
**Case Status:** Escalated to L2 – True Positive

---

## 1. Summary
A suspicious email was flagged by the SIEM as potentially malicious.  
The email appeared to originate from **Microsoft**, attempting to trick the recipient into downloading and opening a `.rar` attachment.

---

## 2. Initial Alert
- **Detection Source:** SIEM – Suspicious Email Alert
- **Alert Trigger:** Malicious attachment detected in inbound email
- **Recipient:** Internal user (redacted)
- **Subject Line:** [REDACTED] – contained urgency keywords
- **Attachment:** `document_info.rar`

---

## 3. Investigation Steps
1. **Header Analysis:**  
   - SPF: **Fail**  
   - DKIM: **Fail**  
   - DMARC: **Fail**  
   - Sending IP did not match legitimate Microsoft ranges.

2. **Attachment Review:**  
   - File type: `.rar` archive  
   - Contained an obfuscated `.exe` file (suspicious behavior).

3. **Threat Intelligence Check:**  
   - Hash matched known malicious sample in VirusTotal and Hybrid Analysis.

4. **User Verification:**  
   - User confirmed they had not requested or expected the email.

5. **SIEM Correlation:**  
   - No previous incidents from same sender, but domain flagged in OSINT feeds.

---

## 4. Actions Taken
- Quarantined the email via email security gateway.
- Blocked sender’s domain and originating IP in firewall.
- Escalated incident to **L2 Analyst** for deeper malware analysis.
- Advised user not to open similar attachments and provided awareness tips.

---

## 5. Outcome
- **Confirmed True Positive** – malicious phishing attempt.
- No compromise detected on recipient endpoint.
- Preventative measures applied to block recurrence.

---

## 6. Recommendations
- Enforce stricter attachment filtering for `.rar` files.
- Increase user awareness training regarding unexpected email attachments.
- Review and tighten SPF/DKIM/DMARC enforcement policies.

---

**Tags:** #Phishing #SOCAnalyst #IncidentResponse #SIEM #EmailSecurity
