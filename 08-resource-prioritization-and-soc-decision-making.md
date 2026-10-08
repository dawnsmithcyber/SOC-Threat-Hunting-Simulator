# 08 — Resource Prioritization & SOC Decision-Making

---

## ⚖️ Security Is a Prioritization Problem

One of the most realistic lessons from this simulation was that I rarely had enough resources to address everything at once.

At different points, I had to work within constraints involving:

- Limited staff
- Limited budget
- Multiple vulnerable systems
- Competing remediation tasks
- Operational dependencies
- Systems already assigned to other work
- OT/ICS restrictions
- Actions requiring prerequisites
- New incidents changing priorities

The question was no longer simply:

**"What needs to be fixed?"**

It became:

**"What should we address first with the resources available right now?"**

That required risk-based decision-making.

---

## 🧠 Every Decision Had a Tradeoff

Several actions might improve security, but they did not necessarily carry the same urgency.

For example, available actions could include:

- Changing default credentials
- Installing antivirus
- Adding Endpoint Detection
- Applying system patches
- Hardening systems
- Updating firmware
- Creating restore points
- Conducting vulnerability scans
- Responding to an active incident

All of these can provide value.

But trying to do everything at once was impossible.

I had to consider:

**Risk → Asset Criticality → Exposure → Dependencies → Operational Impact → Resources**

This changed the way I approached each turn.

Instead of asking:

**"What security control can I add?"**

I started asking:

**"Which action reduces the most meaningful risk right now?"**

---

## 🚨 Incidents Can Immediately Change Priorities

The ransomware incident involving **KHAMMOND36** demonstrated this clearly.

Before the incident, resources could be assigned toward improving the environment.

Once ransomware appeared, priorities changed.

The immediate focus became:

**Activate Incident Response → Disconnect the affected system → Gather Forensics**

Long-term improvements were still important.

But an active compromise required immediate containment and investigation.

This reinforced an important SOC principle:

**Priorities must change when the threat landscape changes.**

A remediation plan cannot be so rigid that analysts fail to respond to an active incident.

---

## 🔑 Credentials Before Hardening

One decision that became particularly important during the simulation involved systems still using default credentials.

Hardening a system improves its security configuration.

But if that same system still has default credentials, an attacker may already have a simple path to access it.

That led me to prioritize:

**Change Default Credentials → Harden the System**

This was an important shift in my thinking.

I stopped viewing security controls as isolated tasks and started considering the order in which they should be implemented.

The question became:

**"What weakness gives an attacker the easiest path into this system?"**

Addressing that weakness first can reduce immediate exposure before additional hardening is performed.

---

## 🩹 Patch First, Then Add Additional Protection

The same sequencing logic applied to vulnerable systems.

For **DMZHISTORIAN**, I recommended:

**Patch first → Then install antivirus**

Antivirus adds another defensive layer, but it does not replace remediation of a known vulnerability.

If a patch is available and operationally safe to deploy, removing the vulnerability addresses the underlying weakness.

Additional endpoint protection can then strengthen the system further.

This reinforced another principle:

**Security controls should complement remediation, not substitute for it when remediation is available.**

---

## 🏭 OT/ICS Changed the Risk Equation

One of the most important lessons came from the operational technology portion of the environment.

Earlier in the simulation, firmware was updated on the **S76100-7 PLC** without the required ICS Vendor Patch Certification.

The result was significant:

**The PLC went out of service.**

That decision affected production and demonstrated something critical:

**A technically valid security action can still create operational risk.**

In an enterprise IT environment, patching quickly may often be desirable.

In an OT/ICS environment, additional considerations may include:

- Vendor certification
- Equipment compatibility
- Production availability
- Safety
- Maintenance windows
- Recovery capability
- Operational dependencies

The lesson was not:

**"Do not patch OT systems."**

The lesson was:

**Understand the environment before making the change.**

---

## 🔄 Recovery Capability Became Part of the Decision

After seeing the operational consequences of a failed change, I began paying much closer attention to recovery.

Before making certain changes, I considered whether a restore point or other recovery capability should exist first.

My thought process became:

**Change Needed → Check Dependencies → Verify Recovery → Implement → Validate**

That adds another question to remediation planning:

**"If this change fails, how do we recover?"**

Security improvements should not create unnecessary operational instability.

---

## 🎯 Asset Criticality Matters

Not every system carries the same level of business or security risk.

For example, **AD-SERVER** represents a particularly important asset because Active Directory supports identity and access across the environment.

A compromise involving a high-value identity system can potentially affect many other systems.

That means remediation decisions should consider not only the vulnerability itself, but also:

- What the asset does
- Who depends on it
- What privileges it controls
- What data it can access
- What other systems trust it
- What an attacker could reach from it

This is why vulnerability prioritization cannot rely on severity alone.

**Context changes risk.**

---

## 👁️ When I Could Not Patch, I Increased Visibility

Later in the simulation, vulnerabilities remained on **AD-SERVER** and **ENGWS66**, but no patch was currently available.

At that point, I could not eliminate the vulnerability.

So I asked a different question:

**"What can I do to reduce risk while remediation is unavailable?"**

I recommended adding **Endpoint Detection** to both systems.

That did not fix the vulnerabilities.

Instead, it provided additional visibility into activity occurring on those assets.

This introduced me to the practical value of **compensating controls**.

When the preferred remediation is unavailable, another control may help reduce exposure or improve the ability to detect suspicious activity.

---

## 🧩 Dependencies Matter

The simulation repeatedly showed that some actions depended on other actions being completed first.

Examples included:

**Certification → OT Change**

**Restore Capability → Higher-Risk Change**

**Patch → Additional Endpoint Protection**

**Credential Change → Hardening**

Ignoring dependencies could create unnecessary risk or waste limited resources.

Before recommending an action, I began asking:

**Is this action actually ready to be performed?**

That simple question prevented me from treating the security board like a checklist.

---

## 👥 Limited Staff Forced Better Decisions

There were turns where several systems required attention but only a few people were available.

That meant every assignment had an opportunity cost.

If I assigned one person to a lower-priority task, that person was no longer available for something more urgent.

My decision process became:

**What is urgent?**

**What creates the greatest risk?**

**What can actually be completed right now?**

**What has prerequisites?**

**What can safely wait?**

**What gives us the greatest risk reduction for the resources used?**

This is where the simulation began feeling less like a technical checklist and more like SOC decision-making.

---

## 💰 Budget Is Also a Security Constraint

Staff availability was not the only limitation.

Some controls required spending from a finite budget.

That meant I also had to consider whether the security benefit justified the cost.

The cheapest option was not automatically the best option.

The most expensive option was not automatically the strongest option.

The goal was to use available resources where they could reduce the most meaningful risk.

That required balancing:

**Security Value + Business Impact + Cost + Timing**

---

## 📊 My Prioritization Framework

By this stage of the simulation, I had developed a much clearer decision process.

When multiple actions competed for limited resources, I considered:

### 1. Active Threat

Is there an incident occurring right now?

If yes, containment and investigation may immediately become the priority.

### 2. Exposure

Is there an obvious weakness such as default credentials or an exploitable vulnerability?

### 3. Asset Criticality

How important is the affected system to identity, production, business operations, or security?

### 4. Remediation Availability

Can the underlying weakness actually be fixed?

### 5. Dependencies

Does the action require certification, recovery preparation, another task, or operational approval first?

### 6. Operational Risk

Could the security change disrupt production or create another problem?

### 7. Compensating Controls

If remediation is unavailable, can detection, monitoring, segmentation, or another control reduce risk?

### 8. Resources

How many people, how much time, and how much budget are available?

Then I make the best decision possible with the information available.

---

## 🧭 Prioritization Is Not Static

One of the biggest lessons from the simulator was that the "right" priority can change.

A system that was lower priority yesterday may become critical today because:

- A new vulnerability appears
- An attack occurs
- New threat intelligence becomes available
- Another control fails
- A dependency is completed
- A patch becomes available
- The business environment changes

SOC decision-making requires continuous reassessment.

**Prioritize → Act → Validate → Reassess**

Then repeat.

---

## 💬 Interview Talking Point

> "One of the strongest lessons I took from the simulation was how much security depends on prioritization. We had limited staff, budget, competing vulnerabilities, operational dependencies, and eventually an active ransomware incident. I learned that I could not simply choose the next item on a list. I had to consider asset criticality, exposure, prerequisites, operational impact, and what would reduce the most meaningful risk. The OT portion reinforced this when a PLC firmware update caused an outage because the required vendor certification had not been completed. Later, when vulnerabilities remained on systems such as AD-SERVER and ENGWS66 without an available patch, I shifted to compensating controls and recommended Endpoint Detection to increase visibility. That helped me understand that good SOC decision-making is not about fixing everything at once. It is about making the best defensible risk decision with the resources and information available."

---

## 🔑 Key Takeaway

**The SOC will almost never have unlimited people, time, or budget.**

The goal is not to do everything.

The goal is to understand the environment well enough to determine:

**What must happen now.**

**What should happen next.**

**What can safely wait.**

**And why.**

That is risk-based security decision-making.

---

## Next Case Study

➡️ **09 — Defense in Depth & Security Control Strategy**
