# 09 — Defense in Depth & Security Control Strategy

---

## 🛡️ Security Is Stronger in Layers

One of the clearest lessons from this simulation was that no single security control could protect the entire environment.

Throughout the exercise, I worked with multiple defensive controls, including:

- Multi-Factor Authentication
- Strong Wi-Fi security
- Default credential changes
- System hardening
- Vulnerability scanning
- System patching
- Firmware updates
- Antivirus
- Endpoint Detection
- Log Collection & Analysis
- Security Awareness
- Incident Response
- Restore Points

Each control addressed a different type of risk.

The value came from how those controls worked together.

This demonstrated the practical concept of **Defense in Depth**:

> Security should not depend on a single defensive control. Multiple layers should work together so that if one control fails, others can still prevent, detect, contain, or help recover from an attack.

---

## 🔐 Identity Was One Layer

Early in the simulation, identity and credential weaknesses represented an obvious attack path.

Controls such as:

**Multi-Factor Authentication**

and

**Changing Default Credentials**

helped reduce the likelihood that an attacker could gain access simply through compromised, weak, or known credentials.

But identity controls alone were not enough.

Even strong authentication would not remediate:

- An exploitable software vulnerability
- An unpatched system
- Malicious activity already occurring on an endpoint
- Unsafe OT changes
- Malware executing after initial access

Identity therefore became one layer of a larger defensive strategy.

---

## 🩹 Patching Removed Known Weaknesses

Patching provided another defensive layer.

When a vulnerability had an available and operationally safe patch, remediation could remove the underlying weakness rather than simply attempting to detect exploitation.

This led to a basic sequence I repeatedly considered:

**Identify Vulnerability → Evaluate Risk → Verify Prerequisites → Patch → Validate**

However, the simulation also demonstrated that patching could not always happen immediately.

Some systems had operational dependencies.

Some required certification.

Others had vulnerabilities for which remediation was not currently available.

That meant another layer was necessary.

---

## 👁️ Detection Helped Cover What Could Not Be Immediately Fixed

Later in the simulation, vulnerabilities remained on systems such as **AD-SERVER** and **ENGWS66**, but no patch was currently available.

I could not eliminate the vulnerabilities.

Instead, I recommended adding **Endpoint Detection**.

This did not remediate the underlying weakness.

It increased visibility into activity occurring on those systems and provided another opportunity to identify suspicious behavior.

This demonstrated the value of **compensating controls**.

When prevention or remediation is unavailable, detection and monitoring can help reduce risk while the organization waits for a permanent fix.

---

## 📊 Logs Turned Individual Events Into Visibility

Endpoint protection alone does not provide the entire picture.

Log Collection & Analysis created another important layer by allowing activity across systems to be observed and investigated.

Logs can help analysts identify patterns such as:

- Repeated authentication failures
- Unexpected account activity
- Suspicious process execution
- Network connections
- Changes to systems
- Security control failures
- Activity occurring across multiple assets

This reinforced an important distinction:

**Prevention attempts to stop an attack.**

**Detection helps identify when prevention may have failed.**

A mature security strategy needs both.

---

## 🚨 Incident Response Became the Containment Layer

The ransomware incident involving **KHAMMOND36** demonstrated what happens when preventive controls are no longer enough.

At that point, the priority shifted to:

**Activate Incident Response → Disconnect the System → Gather Forensics**

Defense in depth therefore extended beyond prevention and detection.

It also included the ability to:

**Contain → Investigate → Recover**

The objective was no longer simply preventing compromise.

It was limiting the damage once compromise occurred.

---

## 🔄 Recovery Became Another Security Layer

The PLC outage also changed how I thought about recovery.

A security change itself can create operational problems if something goes wrong.

That made restore capability part of my security decision-making.

Before higher-risk changes, I began considering:

**Do we have a recovery path if this fails?**

Where appropriate, restore points provided another layer of resilience.

Defense in depth was therefore not only about stopping attackers.

It was also about maintaining the ability to recover when:

- An attack succeeds
- A system fails
- A configuration change causes problems
- A patch creates instability

---

## 🏭 OT/ICS Required Different Defensive Thinking

The operational technology portion of the environment demonstrated that security controls cannot always be applied identically across every system.

The **S76100-7 PLC** outage showed why.

Updating firmware without the required ICS Vendor Patch Certification caused the PLC to go out of service.

The security action itself was reasonable.

The timing and prerequisites were not.

For OT/ICS systems, defense in depth also required considering:

- Vendor requirements
- Operational availability
- Production impact
- Equipment compatibility
- Recovery capability
- Safety
- Change windows

This reinforced that security controls must support the environment they are protecting.

A control that reduces cyber risk but creates unacceptable operational risk may not be the correct action at that moment.

---

## 🧱 The Layers Began Working Together

By the later stages of the simulation, I was no longer looking at controls individually.

I began seeing them as interconnected defensive layers:

**Identity Security**  
↓  
MFA + Credential Management

**Exposure Reduction**  
↓  
Patching + Firmware Updates + System Hardening

**Endpoint Protection**  
↓  
Antivirus + Endpoint Detection

**Visibility**  
↓  
Log Collection + Vulnerability Scanning + Monitoring

**Human Layer**  
↓  
Security Awareness

**Response**  
↓  
Incident Response + Containment + Forensics

**Recovery**  
↓  
Restore Points + Recovery Planning

No single layer guarantees security.

Together, they make it more difficult for an attacker to move from initial access to successful impact without being prevented, detected, contained, or disrupted.

---

## 🧠 My Thinking Changed During the Simulation

At the beginning, it was easy to view the board as a collection of security tasks:

Patch this.

Harden that.

Install antivirus.

Change credentials.

Run a scan.

As the simulation progressed, I began asking a different question:

**"What layer of defense is currently weakest, and what happens if that control fails?"**

That changed how I evaluated recommendations.

Instead of simply adding another security tool, I considered how each action contributed to the overall defensive strategy.

---

## 🔗 Prevention, Detection, Response & Recovery

The simulator ultimately helped me organize security controls into four broader functions:

### Prevention
Reduce the likelihood of successful compromise.

Examples:

- MFA
- Credential changes
- Patching
- Hardening
- Security awareness

### Detection
Identify suspicious or malicious activity.

Examples:

- Endpoint Detection
- Antivirus
- Log Collection & Analysis
- Vulnerability scanning

### Response
Limit damage once suspicious activity or compromise is identified.

Examples:

- Incident Response activation
- System isolation
- Forensic investigation

### Recovery
Restore operations safely after an incident or failed change.

Examples:

- Restore points
- Recovery planning
- Validation after remediation

A resilient environment needs capabilities across all four.

---

## 💬 Interview Talking Point

> "The simulator helped me understand defense in depth as more than simply deploying multiple security tools. I saw how identity controls, patching, hardening, endpoint detection, logging, incident response, and recovery all addressed different parts of the attack lifecycle. One example was when vulnerabilities remained on AD-SERVER and ENGWS66 but patches were unavailable. Instead of treating that as a reason to do nothing, I recommended Endpoint Detection as a compensating control to increase visibility. The ransomware event reinforced the next layer because once prevention failed, containment and forensic investigation became the priority. The exercise taught me to think about what happens when each control fails and what other defensive layer is available."

---

## 🔑 Key Takeaway

**Defense in depth is not about adding as many security tools as possible.**

It is about creating complementary layers that reduce the chance that one failure becomes a complete compromise.

The question is not only:

**"What control can stop this?"**

It is also:

**"If this control fails, what happens next?"**

That mindset connects prevention, detection, response, and recovery into one security strategy.

---

## Next Case Study

➡️ **10 — Final Lessons Learned: Thinking Like a SOC Analyst & Threat Hunter**
