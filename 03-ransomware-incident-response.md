# 03 — Ransomware Incident Response

---

## 🚨 The Incident

As the simulation progressed, the environment moved from preventative security work into active incident response.

Ransomware impacted **KHAMMOND36**.

At that point, the priority changed immediately.

We were no longer deciding which preventative control would provide the greatest long-term risk reduction. We now had an active security incident where containment, investigation, and recovery had to take priority.

> **When an incident becomes active, priorities change. Stop the spread, preserve what you can, investigate what happened, and recover safely.**

---

## 🛑 First Priority — Containment

My first concern was preventing the incident from spreading beyond the affected asset.

The response included:

- Activating Incident Response
- Disconnecting the affected system
- Gathering forensic evidence
- Preparing for recovery

Disconnecting the affected asset was important because an infected endpoint could potentially become a pivot point into other systems.

The immediate question was:

**How do we prevent one compromised system from becoming multiple compromised systems?**

This reinforced an important incident-response principle for me:

> **Containment may temporarily disrupt operations, but allowing an attacker to continue operating can create far greater impact.**

---

## 🔎 Preserve Evidence Before Moving On

Containment was only part of the response.

We also chose to **Gather Forensics**, using available staff and budget to preserve information about the incident.

That decision mattered because simply replacing or restoring an affected system can remove valuable evidence.

Without evidence, we may recover the machine while losing the opportunity to understand:

- How the attacker entered
- What occurred before the ransomware executed
- Whether credentials were compromised
- Whether the attacker moved laterally
- Whether other systems were contacted
- Whether persistence existed elsewhere
- Whether additional assets were affected

This changed the way I thought about recovery.

> **Restoring the asset does not automatically mean the incident is over.**

---

## 🧭 Hunting Backward From Impact

Ransomware is often the visible **impact** of an attack, not necessarily the beginning of it.

Seeing ransomware on KHAMMOND36 tells me where the attack became obvious.

It does not tell me where the attack started.

That creates the threat-hunting question:

**What happened before the ransomware executed?**

Instead of beginning and ending the investigation with the ransomware event, I would work backward through the available telemetry and build a timeline.

A simplified investigation path would look like:

**Ransomware Execution ← Suspicious Process Activity ← Lateral Movement or Remote Access ← Credential Activity ← Initial Access**

The exact path would depend on the evidence available, but the objective would remain the same:

> **Reconstruct the attack story rather than investigate the final event in isolation.**

---

## 🔬 What I Would Hunt For

Using available endpoint, authentication, network, and SIEM telemetry, I would look for activity preceding the ransomware event.

### Endpoint Activity

I would investigate:

- Suspicious processes or process trees
- PowerShell or command-line activity
- Newly created executables or scripts
- Unexpected scheduled tasks or services
- Security tools being disabled
- File encryption activity
- Attempts to delete backups or recovery mechanisms

### Authentication Activity

I would look for:

- Unusual successful logins
- Multiple failed logins followed by success
- Authentication from unexpected systems
- Privileged account usage
- Logins occurring at unusual times
- Accounts authenticating to multiple systems unexpectedly

### Network Activity

I would review:

- Connections between KHAMMOND36 and other assets
- Unexpected outbound connections
- Connections immediately preceding encryption
- Internal systems contacted by the affected host
- Possible command-and-control traffic
- Evidence of lateral movement

The goal would be to determine whether KHAMMOND36 was:

**the initial compromise, an intermediate system, or simply where the attacker finally revealed themselves.**

---

## 🧠 From Alert Triage to Attack Story

This incident reinforced one of the most important lessons of the simulation for me.

An alert tells me **something happened**.

An investigation asks **what happened**.

Threat hunting goes further and asks:

**What else happened that we have not detected yet?**

That distinction changes the investigation from:

**KHAMMOND36 has ransomware.**

to:

**How did ransomware reach KHAMMOND36, what happened before encryption, and where else might the attacker have gone?**

That is the difference between investigating an event and reconstructing an attack.

---

## 🛠️ Recovery

The affected asset was ultimately replaced as part of the recovery process.

But recovery should not simply mean returning a system to service.

Before considering an incident fully resolved, I would want confidence that:

- The compromised asset was contained
- Relevant forensic evidence was preserved
- The likely attack path was investigated
- Potentially compromised credentials were addressed
- Related systems were reviewed for suspicious activity
- Persistence mechanisms were not present elsewhere
- The recovered or replacement system was returned to a known-good state

This produces a more complete incident-response sequence:

**Detect → Contain → Preserve Evidence → Investigate → Eradicate → Recover → Validate → Hunt**

---

## 🔄 The Lesson After Recovery

One of the easiest mistakes during incident response is allowing restoration of service to become the finish line.

Operationally, restoring the system matters.

From a security perspective, however, another question remains:

**Did we remove the attacker, or did we only remove the damage we could see?**

That question is where incident response and threat hunting intersect.

After recovery, I would continue looking for evidence of activity on surrounding systems and for indicators that preceded the ransomware event.

> **Recovery restores operations. Validation and hunting help determine whether the threat is actually gone.**

---

## 💬 Interview Talking Point

> "During the simulation, ransomware impacted KHAMMOND36 and our priorities immediately shifted from preventative security work to incident response. We activated IR, isolated the affected asset, and gathered forensic evidence before moving through recovery. The biggest lesson for me was that ransomware represents an impact, but not necessarily the beginning of the attack. I would use the available endpoint, authentication, network, and SIEM telemetry to build a timeline backward from encryption and determine how the attacker gained access, whether credentials were involved, whether lateral movement occurred, and whether other systems were affected. Recovery gets the system operational again, but threat hunting helps determine whether the attacker is actually gone."

---

## 🔑 Key Takeaway

**Ransomware may be where the attack becomes visible, but the investigation should not begin there and end there.**

The ransomware event gives me a point in the timeline.

My job is to determine what came before it, what happened around it, and whether the activity extended beyond the system where the impact was discovered.

**Impact → Timeline → Initial Access → Scope → Containment → Recovery → Validation**

That is how an isolated alert begins becoming an attack story.

---

## Next Case Study

➡️ **04 — OT Patching & PLC Lessons**
