# 🛡️ Incident Response Tabletop Exercise – Tim-Force


A comprehensive group-based **Incident Response Tabletop Exercise** simulating a real-world cybersecurity incident at **Tim-Force**, a mid-sized online automotive marketplace.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Organization Profile](#organization-profile)
- [Incident Scenario](#incident-scenario)
- [Our Response Strategy](#our-response-strategy)
- [Key Learnings](#key-learnings)
- [Skills Demonstrated](#skills-demonstrated)
- [Team Members](#team-members)
- [Repository Contents](#repository-contents)

---

## Overview

This tabletop exercise simulated a sophisticated cyberattack on Tim-Force, a fictional automotive marketplace company. Our team analyzed security logs, identified compromised accounts, and developed comprehensive incident response strategies across multiple phases of the attack.

The scenario involved a **legacy service account vulnerability** that led to a "Persistent Ghost" attacker (identified as `tempuser99`) who disrupted critical business systems including the vehicle title processing infrastructure.

---

## Organization Profile

**Tim-Force** is characterized as:

| Attribute | Description |
|-----------|-------------|
| **Industry** | Online Automotive Marketplace (C2C/B2B) |
| **Size** | Mid-sized, fast-scaling technology company |
| **Business Model** | Digital auction platform for dealer-to-dealer used vehicle sales |
| **Services** | Title processing, logistics coordination (TrueGrade, Tim-Force Transport), dealer financing (Tim-Force Capital) |
| **Workforce** | Mostly remote; title processing depends on a single physical location |

### Critical Assets
- Marketplace platform (primary revenue source)
- Customer/dealer PII
- Sensitive financial data
- Secure title printers

### Existing Security Controls
- MFA and SSO integrated with cloud IAM
- Endpoint Detection and Response (EDR)
- Centralized SIEM with automated behavioral alerts
- Isolated production network for auction platform
- Routine vulnerability scans

### Known Vulnerabilities (Pre-Incident)
- Service accounts with limited monitoring and **no MFA**
- Inconsistent offboarding procedures
- Single-point-of-failure for mission-critical printing
- Limited disaster recovery beyond cloud backups

---

## Incident Scenario

### Part 1: The Repeating Breach (Day 1-2)

Tim-Force's SOC detected an unusual pattern of compromised accounts. Key observations included:

- Every secured account showed new unauthorized logins within 24 hours
- Logins appeared from unusual geolocations and outside business hours
- All affected users had interacted with a deprecated internal tool linked to a **legacy service account exempt from MFA**

**Anomalies Detected:**
- Failed login attempts followed by successful ones within minutes
- Temporary user accounts appearing and vanishing from logs
- Mysterious account `system.tempuser99` active in logins but absent from IAM

### Part 2: Persistent Ghost (Day 3-5)

Despite credential rotation and account disabling, intrusions continued:

- The ghost account remained visible in log activity
- Attacker scanned internal documentation focused on title processing workflows
- Removal attempts failed; account reappeared within hours
- Behavioral analysis suggested escalating access privileges
- Title processing began experiencing delays
- Evidence suggested attacker manipulation of internal alerting systems

---

## Our Response Strategy

### Phase 1: Initial Response (Day 1-2)

**Immediate Actions:**
1. Disable compromised legacy service accounts
2. Back up critical accounts and system states
3. Pull logs from IAM, legacy systems, and firewalls
4. Deploy SIEM tools (Splunk) for user behavior analysis

**Containment Measures:**
- Rotate passwords across affected accounts
- Enforce MFA wherever possible
- Enable monitoring with alerts on critical systems
- Block suspicious IP addresses and geolocations using IDS/IPS
- Implement network segmentation

**Business Decision:** Continue critical operations (auction platform, title processing) while quietly tightening internal security controls and limiting access to critical systems.

### Phase 2: Escalated Response (Day 3-5)

**Aggressive Isolation:**
- Network segmentation around title processing platform
- Eliminate persistence techniques
- Enable least-privilege access
- Identify escalation tools being used
- Prepare for system downtime

**Exfiltration Verification:**
- Deep SIEM log analysis
- Network traffic analysis
- Threat intelligence mapping
- Focus on title processing document exfiltration

**Escalation Protocol:**
- **Internal:** Notify CEO, CISO, and business owners
- **External:** Alert cyber insurance provider; communicate with partners
- **Proactive:** Prepare customer communication templates

### Phase 3: Recovery

1. Restore title processing from verified backups
2. **Mandate MFA** across all systems
3. Implement least-privilege access model
4. Carefully reopen and monitor business operations

---

## Key Learnings

| Lesson | Description |
|--------|-------------|
| **Attackers Adapt Fast** | Persistence mechanisms allowed rapid reentry after initial containment |
| **Legacy Systems = Major Risk** | Unmonitored service accounts without MFA created the initial attack vector |
| **Detection Needs Improvement** | Anomaly detection capabilities must be enhanced |
| **MFA is Non-Negotiable** | Universal MFA enforcement prevents credential-based attacks |

### Business Impact Assessment

Delayed or disrupted title processing creates significant risks:
- **Revenue Loss** – halted vehicle sales
- **Customer Dissatisfaction** – loss of dealer and buyer confidence
- **Reputational Damage** – long-term customer loss
- **Regulatory Penalties** – PII and financial data exposure triggers compliance issues

---

## Skills Demonstrated

- **Incident Response** – Detection, analysis, containment, eradication, and recovery
- **Identity and Access Management (IAM)** – Identifying weaknesses in service accounts and authentication
- **Security Information and Event Management (SIEM)** – Log analysis and behavioral pattern recognition
- **Risk Assessment** – Evaluating business continuity impacts and data exposure risks
- **Security Operations** – Coordinated response across technical and business stakeholders
- **Information Security** – Applying defense-in-depth principles and least-privilege access

---

## Team Members

**Group 7:**

| Name |
|------|
| Faraz Ahmed |
| Pramath Yaji |
| Rohan Dalvi |
| Kathiresan Kandasamy |
| Bhuvantej Ramachandra Reddy |

---

## Repository Contents

```
📁 TimForce-Incident-Response/
├── 📄 README.md                      # This file
├── 📁 docs/
│   ├── 📄 InfoSec_Tabletop_ques.pdf  # Case study/scenario (provided by professor)
│   └── 📄 InfoSec_TTX.pdf            # Team presentation slides
└── 📁 assets/
    └── 🖼️ linkedin_preview.png       # LinkedIn project preview
```

---

## 📚 References

- NIST Cybersecurity Framework
- SANS Incident Response Process
- MITRE ATT&CK Framework (Persistence Techniques)

---

