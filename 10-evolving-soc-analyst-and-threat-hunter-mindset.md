# 10 — Evolving SOC Analyst & Threat Hunter Mindset

---

## 🧠 From Completing Tasks to Making Security Decisions

One of the biggest changes for me during this simulation has been how I approach the board itself.

Early in the exercise, many decisions appeared straightforward:

- Patch vulnerable systems
- Change default credentials
- Install antivirus
- Harden devices
- Run vulnerability scans
- Enable additional security controls

As the environment became more complex, I learned that identifying the technically correct security action was only part of the problem.

I also had to determine:

- Which risk should be addressed first?
- What assets are most critical?
- What dependencies exist?
- Could the security action disrupt operations?
- Do we have the people and budget available?
- What happens if the remediation fails?
- What can we do when the vulnerability cannot currently be fixed?

That shift changed the way I approached the simulation.

Instead of asking only:

> "What security control should I deploy?"

I began asking:

> "What is the greatest risk right now, and what is the safest and most effective way to reduce it?"

---

## 🎯 Prioritization Became Part of the Investigation

The simulator repeatedly forced me to make decisions with limited staff, budget, and time.

Not every vulnerability could be addressed immediately.

Not every security control could be deployed at once.

That meant recommendations had to be prioritized based on risk rather than simply completing everything visible on the board.

I began considering:

**Asset Criticality → Exposure → Vulnerability → Operational Impact → Available Controls → Resources**

This became especially important when multiple systems required attention simultaneously.

The goal was no longer simply to complete security tasks.

The goal became determining which action reduced the most meaningful risk with the resources available.

---

## 🔎 I Started Looking Beyond the Alert

The simulation also reinforced an important threat hunting mindset:

An individual alert or vulnerability does not always tell the entire story.

A vulnerable system may also have:

- Weak credentials
- Missing endpoint protection
- Limited logging
- Poor hardening
- Operational dependencies
- Connections to other critical systems

Looking at these conditions together provides a much better understanding of risk than looking at each issue independently.

This encouraged me to think beyond individual events and ask:

> "What story is the environment telling me?"

That mindset closely reflects how I want to approach threat hunting:

**Stop hunting events. Hunt the story.**

---

## 🧩 Dependencies Changed My Decision-Making

One of the strongest lessons came from the OT/ICS portion of the environment.

The S76100-7 PLC outage demonstrated that a technically valid security action can still create operational risk when prerequisites are ignored.

Updating firmware without the required ICS Vendor Patch Certification caused the PLC to go out of service.

That changed how I approached later recommendations.

Before recommending changes, I began checking for:

- Required certifications
- Vendor requirements
- Restore capability
- Operational dependencies
- Production impact
- System location
- Available staff
- Change sequencing

The lesson was simple but important:

> A security control is only effective if it can be implemented safely in the environment it is protecting.

---

## 🛡️ When Remediation Wasn't Available, I Looked for Another Layer

Another important shift occurred when vulnerabilities remained on systems such as **AD-SERVER** and **ENGWS66**, but patches were not currently available.

The vulnerability still existed.

Doing nothing was not the only option.

I recommended **Endpoint Detection** as a compensating control.

It would not remove the vulnerability, but it could increase visibility into suspicious activity while the organization waited for a permanent remediation option.

This reinforced a mindset I expect to carry into SOC and threat hunting work:

> If I cannot eliminate the risk immediately, what can I do to reduce exposure or improve my ability to detect exploitation?

---

## 🚨 Incidents Changed the Priority Immediately

The ransomware incident involving **KHAMMOND36** demonstrated how quickly priorities can change.

Once compromise occurred, routine security improvements were no longer the immediate concern.

The priority became:

**Activate Incident Response → Disconnect the System → Gather Forensics**

The incident reinforced that analysts must be able to shift from prevention to containment and investigation quickly.

Security priorities are not static.

They change based on what is happening in the environment.

---

## 🔄 I Learned to Think About What Comes Next

Another major change in my thinking was learning not to view a security action as the end of the process.

After remediation, I began considering:

- Did the change work?
- Did it create another problem?
- Should the system be rescanned?
- Do we need additional monitoring?
- Is another defensive layer still missing?
- Do we have a recovery path?

This turned individual actions into a larger cycle:

**Identify → Prioritize → Remediate → Validate → Monitor → Reassess**

That cycle is much closer to how security operations function in a real environment.

---

## 👥 Working as Part of a SOC Team

The simulator has also reinforced that security decisions are rarely made in isolation.

Recommendations were discussed with other participants, challenged, clarified, and adjusted as new information became available.

Sometimes another team member identified a dependency.

Sometimes new information changed which system should be addressed first.

Sometimes the best decision was to wait.

That process reinforced the importance of:

- Communicating reasoning clearly
- Asking questions when information is incomplete
- Accepting new evidence
- Adjusting recommendations
- Supporting team decisions
- Documenting why an action was recommended

Being able to explain **why** became just as important as knowing **what** action to take.

---

## 🧠 My Analyst Mindset So Far

At this stage of the simulation, my thought process has evolved into something closer to:

**What happened?**

↓

**What is exposed?**

↓

**What is the greatest risk?**

↓

**What systems or business operations could be affected?**

↓

**What controls are already protecting the asset?**

↓

**What control is missing?**

↓

**Can remediation be performed safely?**

↓

**If not, what compensating control can reduce risk?**

↓

**How will we validate the result?**

↓

**What should we monitor next?**

This is the mindset I want to continue developing throughout the remainder of the simulation.

---

## 💬 Interview Talking Point

> "One of the biggest things the SOC simulator has taught me is that security operations are not about completing a checklist of controls. I have had to prioritize vulnerabilities, respond to ransomware, work around unavailable patches, account for OT dependencies, manage limited staff and budget, and explain the reasoning behind my recommendations. Over time, I stopped looking at each issue individually and started looking at how the systems, vulnerabilities, controls, and operational risks connected. That is also how I approach threat hunting — I do not want to look at one event in isolation. I want to understand the story the environment is telling me."

---

## 🔑 Key Takeaway

**My biggest lesson so far is that good security decisions require context.**

The most technically obvious action is not always the correct action at that moment.

A SOC analyst must understand the threat, the asset, the vulnerability, the available controls, the operational impact, and the resources available before deciding what happens next.

And when the environment changes, the analyst must be willing to change the plan.

---

## 🚧 This Case Study Is Still in Progress

This repository documents lessons from an ongoing **75-day SOC / Threat Hunting simulation**.

The exercise is not complete.

New incidents, vulnerabilities, operational challenges, defensive controls, and team decisions may change or expand the lessons documented here.

As the simulation continues, additional case studies and findings will be added.

**Current objective: Keep learning. Keep investigating. Keep asking why.**
