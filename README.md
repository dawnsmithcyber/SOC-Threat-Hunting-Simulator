# 🔎 SOC Threat Hunting & Incident Response Case Study

## 75-Day IT/OT Security Operations Simulation

> **Stop hunting events. Hunt the story.**

This repository documents my participation in a **75-day, team-based SOC simulation** involving a fictional manufacturing environment with both Information Technology (IT) and Operational Technology (OT) assets.

Rather than simply documenting which security controls were selected, this case study focuses on the **reasoning behind the decisions** — identifying risk, prioritizing remediation, responding to incidents, analyzing operational impact, validating defensive changes, and determining when additional detection or threat hunting was warranted.

---

## 🎯 Project Objective

The goal of this project is to demonstrate how I approach security operations when multiple risks compete for limited resources.

Throughout the simulation, our team must balance:

- Active security threats
- Vulnerability remediation
- Identity and credential security
- Incident response
- Endpoint visibility
- IT and OT availability
- Limited personnel
- Budget constraints
- Operational impact

The exercise reinforces an important SOC principle:

**The highest-severity issue is not always the first action you should take. Context matters.**

---

## 🔎 My Analyst Approach

My recommendations throughout the simulation follow a risk-based process:

**Identify → Prioritize → Investigate → Remediate → Validate → Hunt**

I ask questions such as:

- What asset is affected?
- How critical is that asset?
- Is there evidence of active exploitation?
- What telemetry is available?
- Could remediation disrupt operations?
- Are prerequisites required before making the change?
- What compensating controls can reduce risk if remediation is not immediately possible?
- After remediation, how do we verify that the risk was actually reduced?

This approach shifts the focus from simply reacting to alerts to understanding the **larger attack story**.

---

## 🏭 IT vs. OT Security

One of the most valuable parts of this simulation has been working with both traditional IT systems and Operational Technology.

In IT environments, patching or isolating a vulnerable system may be relatively routine.

In OT, that same action can affect **availability, production, equipment, or physical processes**.

The simulation reinforced that security decisions must consider both:

**Cyber Risk + Operational Risk**

Sometimes the technically obvious security action is not the safest operational decision.

---

## 🚨 Incident Response

The simulation has included an active ransomware incident affecting **KHAMMOND36**.

Our response included:

**Activate Incident Response → Disconnect the Asset → Gather Forensics → Replace/Recover → Validate**

The incident reinforced the importance of containment and evidence preservation while also raising the threat-hunting question:

> What happened before the ransomware became visible?

The encryption event may be the alert — but it may not be the beginning of the attack.

---

## 🔎 Threat Hunting Mindset

Threat hunting throughout this project focuses on moving beyond individual alerts and looking for relationships between:

- Authentication activity
- Endpoint behavior
- Vulnerabilities
- Credential exposure
- Network movement
- Security-control gaps
- Asset criticality
- Incident timelines

When a vulnerability cannot immediately be patched, the investigation does not stop.

That is when **visibility, detection, compensating controls, and threat hunting become even more important.**

---

## ⚙️ OT Lesson Learned

One of our most important lessons came from updating firmware on a PLC before the required **ICS vendor certification** was completed.

The asset went out of service.

That changed how I approached later OT decisions.

Before recommending changes to OT assets, I began considering:

**Prerequisites → Availability → Operational Impact → Security Benefit → Validation**

The lesson was simple but important:

> A security control that reduces cyber risk can still increase operational risk if implemented incorrectly.

---

## 📂 Case Study Series

This repository will grow throughout the 75-day simulation.

### Part 1
[Environment & Risk Baseline](01-environment-and-risk-baseline.md)

Establishing the environment, identifying risk, and determining which defensive actions should be prioritized first.

### Part 2
**Identity & Credential Risk**  
Credential exposure, default credentials, access control, and identity-based attack paths.

### Part 3
**Ransomware Incident Response**  
Containment, forensic collection, recovery, and hunting backward from impact.

### Part 4
**OT Patching & PLC Lessons**  
Why patching decisions in operational environments require additional context.

### Part 5
**Historian Defense**  
Evaluating patching, antivirus, telemetry, and sequencing defensive controls.

### Part 6
**Hunting Unpatchable Risk**  
Using compensating controls and increased visibility when immediate remediation is unavailable.

### Part 7
**Threat Hunting Timeline**  
Connecting individual events to identify patterns and reconstruct potential attack activity.

### Part 8
**Lessons Learned**  
The major SOC, incident response, threat hunting, IT/OT, and risk-prioritization lessons from the exercise.

---

## 🛠️ Skills Demonstrated

`Threat Hunting` • `Incident Response` • `SOC Analysis` • `Risk Prioritization` • `IT/OT Security` • `ICS Security` • `Ransomware Response` • `Endpoint Detection` • `Vulnerability Management` • `Security Monitoring` • `Identity Security` • `Defensive Strategy`

---

## 🧠 Key Takeaway

This simulation continues to reinforce one of the most important lessons I have learned while developing my threat-hunting skills:

**Security operations are not about chasing individual alerts.**

They are about understanding assets, identities, vulnerabilities, telemetry, attacker behavior, and business impact well enough to connect seemingly isolated events into a story.

### 🔎 Stop hunting events. Hunt the story.

---

*This repository documents my individual analysis, recommendations, and lessons learned while participating in a collaborative cybersecurity simulation. The environment and incidents described are simulated and are presented for educational and portfolio purposes.*
