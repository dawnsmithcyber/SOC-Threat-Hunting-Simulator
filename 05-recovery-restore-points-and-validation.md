# 05 — Recovery, Restore Points & Validation

---

## 🔄 Remediation Is Not the Finish Line

One of the biggest changes in my thinking during this simulation was realizing that completing a security action does not necessarily mean the risk has been successfully resolved.

A patch can fail.

A configuration change can break something.

A hardened system can still contain vulnerabilities.

And in an OT environment, even a technically correct change can affect availability or production.

The PLC incident reinforced an important lesson:

> Recovery and validation need to be part of the remediation plan before the change is made — not something considered only after something goes wrong.

That changed the way I approached later decisions in the simulation.

---

## 💾 Why I Started Thinking About Restore Points

After seeing the S76100-7 PLC go out of service following its firmware update, I became much more cautious about making changes without understanding how we would recover if something failed.

Later, when PALALTOPCS required additional security work, I specifically raised the need for a restore point before making changes.

My thinking became:

**Before changing the system, know how you are getting back.**

A restore point does not eliminate the risk of a change, but it gives the team a recovery option if the change creates an unexpected problem.

Before remediation, I would want to know:

- Is there a current restore point or backup?
- Has it been tested?
- What exactly can be restored?
- How long would recovery take?
- What systems depend on this asset?
- Would restoration affect other systems?
- Who needs to approve the change?
- What is the rollback plan if validation fails?

This moved recovery planning from an afterthought to part of my risk assessment.

---

## 🧠 My Decision Process Changed

Earlier in the simulation, my thinking could be simplified as:

**Vulnerability → Remediate**

After the PLC incident, that was no longer enough.

My process became:

**Identify → Assess → Understand Dependencies → Preserve Recovery → Remediate → Validate → Monitor**

Each step answers a different question.

**Identify**  
What vulnerability, weakness, or security issue exists?

**Assess**  
How much risk does it actually create?

**Understand Dependencies**  
What systems, users, or operational processes rely on this asset?

**Preserve Recovery**  
If the change fails, can we safely return the system to a known-good state?

**Remediate**  
What is the safest available action to reduce the risk?

**Validate**  
Did the action actually work?

**Monitor**  
Did anything unexpected happen afterward?

That became a much more realistic way for me to think about security operations.

---

## 🔍 Validation Changed the Meaning of "Done"

One of the most important lessons I took from the simulator was that:

**Action completed ≠ risk resolved**

If I patch a system, I still need to determine whether the vulnerability actually closed.

If I harden a device, I want to know whether the configuration applied correctly.

If I change default credentials, I want to verify that the old credentials no longer work.

If I install endpoint protection, I want to know whether the system is reporting telemetry and actually providing visibility.

If I restore a system, I want to know whether it returned to normal operation.

That means validation should follow remediation.

My workflow became:

**Change → Validate → Re-scan → Monitor**

---

## 🔁 Why Re-Scanning Matters

A vulnerability scan provides a view of the environment at a particular point in time.

Once remediation occurs, that picture may no longer be accurate.

Re-scanning helps answer:

- Did the vulnerability actually disappear?
- Are previously identified weaknesses still present?
- Did the security change introduce a new issue?
- Are there assets that still require remediation?
- Has the overall risk picture changed?

This became especially important as we continued patching and hardening systems throughout the environment.

I did not want to assume that because an action had been completed on the board, the underlying risk was gone.

> Remediation changes the environment. Re-scanning tells me what the environment looks like now.

---

## 🧩 Recovery Is Part of Resilience

I initially thought about backups and restore points primarily as recovery tools.

The simulation helped me understand them as part of security resilience.

Prevention is important.

But prevention will never be perfect.

A resilient environment also needs the ability to:

- Detect problems
- Contain impact
- Recover systems
- Restore operations
- Validate recovery
- Continue monitoring

That means recovery planning belongs inside the security conversation.

This is particularly important when availability matters.

A system that is secure but unavailable may still represent a serious business or operational problem.

---

## 🏭 IT and OT Changed How I Viewed Availability

The OT portion of the simulation made availability much more tangible.

In a traditional IT environment, a failed change may disrupt a workstation, server, application, or business process.

In an OT environment, systems may support physical operations.

That means the question is not simply:

**"Can we fix the vulnerability?"**

I also need to ask:

**"What happens operationally if this system becomes unavailable while we fix it?"**

That changed the way I thought about the CIA triad.

Confidentiality and integrity remain critical, but the simulation made the importance of **availability** much more visible.

---

## 🛡️ Recovery Planning Also Supports Incident Response

Restore points and backups are not only useful when a security change fails.

They can become critical during an actual incident.

If an endpoint is compromised, recovery may require rebuilding or restoring the system.

But before restoring it, I would want to preserve the evidence needed to understand what happened.

That creates an important distinction:

**Recovery and investigation have to be coordinated.**

Restoring too quickly could destroy useful forensic evidence.

Waiting too long could unnecessarily extend operational impact.

The decision therefore depends on:

**Incident severity + evidence requirements + business impact + recovery capability**

That is where incident response becomes more than simply "get the system back online."

---

## 🔎 Threat-Hunting Perspective

Recovery also creates an opportunity for threat hunting.

If a compromised or vulnerable system is restored, patched, or rebuilt, I would not automatically assume the threat disappeared with it.

I would want to investigate:

**What happened before the remediation?**

and:

**What happened after it?**

That could include reviewing:

- Authentication activity
- Process execution
- Network connections
- Changes to accounts or privileges
- Connections to other systems
- Persistence mechanisms
- Lateral movement indicators
- Activity from the original source
- Similar behavior elsewhere in the environment

The goal is to determine whether we fixed only the affected asset or actually removed the attacker's opportunity from the environment.

> Restoring a system fixes the machine. It does not automatically prove the environment is clean.

---

## 🧭 What I Would Validate After a Security Change

My post-change checklist became:

**Operational Validation**
- Is the asset online?
- Is it functioning normally?
- Are dependent systems working?
- Did availability change?

**Security Validation**
- Did the patch or configuration apply?
- Did the vulnerability close?
- Are default credentials gone?
- Are required controls active?
- Is endpoint protection reporting?

**Telemetry Validation**
- Are logs still being generated?
- Is the SIEM receiving them?
- Is endpoint telemetry available?
- Did communication behavior change?

**Risk Validation**
- What risk remains?
- Is another control required?
- Should the asset be monitored more closely?
- Do we need another vulnerability scan?

This prevents "completed" from becoming the same thing as "secure."

---

## 💡 The Bigger Lesson

The simulator changed my thinking from:

**Fix the problem.**

to:

**Fix the problem safely, prove the fix worked, and make sure we can recover if it did not.**

That distinction matters.

Security operations involve systems that people and organizations depend on.

Every change has a technical consequence and potentially an operational consequence.

The analyst's responsibility is not simply to recommend the strongest security control.

It is to understand the environment well enough to recommend the **right control at the right time and verify the outcome.**

---

## 💬 Interview Talking Point

> "One thing the simulation changed for me was how I think about remediation. Early on, I was focused heavily on identifying a vulnerability and fixing it. After a firmware update caused a PLC to go out of service, I started thinking much more about recovery before making the change. Later, I specifically considered restore points before additional remediation and began treating validation as part of the security action itself. My process became identify the risk, understand dependencies, preserve a recovery option, remediate, validate, re-scan where appropriate, and continue monitoring. It taught me that a completed security task does not necessarily mean the risk is resolved."

---

## 🔑 Key Takeaway

**Never make recovery the plan you create after the change fails.**

Know the recovery path before making the change.

Then validate the result.

My mindset became:

**Understand → Protect → Preserve → Change → Validate → Monitor**

Because in security operations:

**"We applied the fix" is not the same as "we reduced the risk."**

---

## Next Case Study

➡️ **06 — Vulnerability Prioritization & Compensating Controls**
