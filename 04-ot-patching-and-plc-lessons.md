# 04 — OT Patching & PLC Lessons

---

## 🏭 When Patching Became an Operational Risk

One of the most important lessons in this simulation came from a decision that initially seemed straightforward:

**A PLC needed a firmware update, so we updated it.**

The asset was the **S76100-7 PLC**.

After the firmware update, however, the PLC went **out of service** and the environment's operational status was negatively affected.

The issue was not that addressing the vulnerability was the wrong security objective.

The problem was that this was an **OT/ICS asset**, and the firmware update was performed before the required **ICS Vendor Patch Certification** was in place.

That changed the way I approached security changes for the rest of the simulation.

> A technically correct security action can still create operational risk if the environment and dependencies are not understood first.

---

## ⚠️ The Mistake

In a traditional IT environment, an available security patch may often lead to a fairly familiar process:

**Assess → Test → Patch → Validate**

OT environments introduce additional considerations.

Industrial systems may control or support physical processes, and availability can be just as important as confidentiality and integrity.

Before making changes to an OT asset, I learned to ask:

- Is this actually an IT asset or an OT/ICS asset?
- What operational process depends on it?
- Is the patch or firmware version vendor approved?
- Are there certification requirements?
- Is there a tested recovery or rollback option?
- Could taking this asset offline affect production?
- Do we understand the dependencies surrounding the device?
- What is the risk of patching compared with the risk of temporarily leaving it unpatched?

The S76100-7 incident demonstrated why those questions matter.

---

## 🧠 Security Risk vs. Operational Risk

The experience forced me to think beyond:

**"Is this system vulnerable?"**

and start asking:

**"What happens to the environment if I change this system?"**

That distinction became especially important in the OT portion of the simulation.

A vulnerability represents security risk.

But remediation itself can introduce operational risk.

The analyst therefore has to consider both.

> The safest security decision is not always the fastest remediation. Sometimes the correct decision is to understand the operational dependency before touching the asset.

---

## 🔄 How My Decision-Making Changed

After the PLC issue, I became much more deliberate about identifying prerequisites before recommending changes.

My process became:

**Identify the vulnerability → Classify the asset → Check prerequisites → Understand operational impact → Preserve recovery options → Remediate → Validate**

This influenced several later decisions in the simulation.

When additional HMI systems and OT-related assets appeared on the board, I did not automatically recommend patching them simply because an update was available.

Instead, I began holding changes when certification requirements were unclear and prioritizing work in other parts of the environment until the OT prerequisites were satisfied.

That was an important shift.

I was no longer treating the board as a list of tasks to complete.

I was treating it as an interconnected environment where one change could affect something else.

---

## 🛡️ Compensating Controls Matter

Sometimes a vulnerability cannot be immediately patched.

That does not mean the only options are:

**Patch it now** or **do nothing**.

If remediation must be delayed, I would look for compensating controls that reduce exposure while the underlying issue remains.

Depending on the environment, those could include:

- Increased endpoint or network monitoring
- Network segmentation
- Restricting unnecessary access
- Reviewing authentication activity
- Limiting administrative privileges
- Monitoring communications involving the affected asset
- Creating detection logic for suspicious behavior
- Increasing logging where possible
- Establishing a known-good restore or recovery point

This became increasingly important later in the simulation when vulnerabilities remained but immediate remediation options were limited.

> If I cannot immediately remove the weakness, I still want to reduce the attacker's opportunity and increase my chance of detecting exploitation.

---

## 🔎 Threat-Hunting Perspective

An unpatched or temporarily unpatchable system creates a useful hunting hypothesis.

Instead of only documenting:

**"This asset has a vulnerability."**

I would ask:

**"Is there evidence that someone is already attempting to exploit it?"**

That means reviewing available telemetry for activity such as:

- Unexpected connections to the vulnerable asset
- Unusual source systems or IP addresses
- New or abnormal authentication activity
- Suspicious processes or commands
- Connections between IT and OT segments that do not match expected behavior
- Changes occurring before or after the vulnerability was identified
- Evidence of reconnaissance or lateral movement
- Activity inconsistent with the asset's normal operational role

The vulnerability becomes more than a remediation ticket.

It becomes a hunting lead.

---

## 🧩 Asset Context Changes Priority

One of the biggest lessons from this portion of the simulation was that vulnerability severity alone does not determine remediation priority.

Context matters.

I would consider:

**Vulnerability severity + exploitability + asset criticality + exposure + operational dependency + available controls**

A high-severity vulnerability on an isolated system may require a different response than the same vulnerability on an exposed system supporting a critical production process.

Likewise, immediately patching a critical OT device without understanding its dependencies may create more operational damage than temporarily mitigating the vulnerability while preparing a safe remediation path.

This is where vulnerability management becomes risk management.

---

## 🔄 Validate After Every Change

Another lesson from the PLC incident was that completing a security action does not mean the action succeeded.

After remediation, I want to validate:

- Is the asset still operational?
- Did the security change apply correctly?
- Did the vulnerability actually close?
- Did the change introduce another problem?
- Are dependent systems functioning normally?
- Did the asset's communication patterns change?
- Do we need to re-scan or re-evaluate the environment?

That changed my mental model from:

**Patch = Done**

to:

**Patch → Validate → Monitor**

---

## 💬 Interview Talking Point

> "One of my biggest lessons from the simulation came from updating firmware on an S76100-7 PLC before the required ICS vendor certification was in place. The device went out of service, which showed me very clearly that OT security decisions have to account for operational impact, not just vulnerability severity. After that, my process changed. I began identifying whether an asset was IT or OT, checking prerequisites and vendor requirements, considering recovery options, and understanding dependencies before recommending remediation. If something could not be safely patched yet, I looked at compensating controls and increased monitoring rather than treating the vulnerability as something we simply had to accept. It taught me that good security is not just about closing vulnerabilities quickly. It is about reducing risk without unnecessarily disrupting the environment."

---

## 🔑 Key Takeaway

**Do not confuse remediation speed with risk reduction.**

The PLC incident taught me that security decisions exist inside an operational environment.

Before changing a critical asset, I need to understand:

**What is vulnerable?**

**What depends on it?**

**What happens if the remediation fails?**

**What controls can reduce risk while we prepare to fix it safely?**

That experience changed my approach from:

**"There is a patch available. Apply it."**

to:

**"Understand the asset, the dependency, and the risk — then choose the safest path to remediation."**

That is a lesson I will carry into real SOC, incident-response, and threat-hunting work.

---

## Next Case Study

➡️ **05 — Recovery, Restore Points & Validation**
