# 01 — Establishing the Defensive Baseline

## 🎯 The Challenge

The simulation began with a manufacturing environment containing both IT and OT assets, limited staff, and a restricted security budget.

That immediately created a realistic SOC problem:

> **We could not fix everything at once. What would reduce the most risk first?**

The early environment presented multiple competing priorities, including asset visibility, vulnerable systems, weak authentication, logging gaps, endpoint protection, Wi-Fi security, patching, and system hardening.

This meant our decisions had to be based on **risk, asset criticality, visibility, and available resources** rather than simply completing a security checklist.

---

## 🔎 My Initial Priorities

Two of my early priorities were:

### 1. 2FA

Strengthening authentication reduced the likelihood that a compromised password alone could provide access to the environment.

From a threat-hunting perspective, identity matters because compromised credentials can become the starting point for:

**Initial Access → Privilege Abuse → Lateral Movement → Persistence**

Protecting identity therefore reduced an important attack path before an incident occurred.

### 2. Log Collection & Analysis

I also prioritized centralized logging because we cannot effectively investigate activity we cannot see.

Logs provide the telemetry needed to establish normal behavior and investigate anomalies across systems.

That visibility becomes critical when trying to answer questions such as:

- Which account authenticated?
- Where did the connection originate?
- Which asset was accessed?
- What happened immediately before and after the event?
- Is the same behavior occurring elsewhere?

---

## 🧠 Threat-Hunting Takeaway

One of my earliest lessons from the simulator was that **threat hunting starts before the hunt itself**.

Before forming a useful hypothesis, I need to understand:

**Assets → Identities → Vulnerabilities → Controls → Telemetry → Expected Behavior**

Asset inventory tells me **what exists**.

Vulnerability mapping tells me **where exposure may exist**.

Centralized logging helps tell me **what those systems are actually doing**.

Without that context, unusual activity is much harder to distinguish from normal behavior.

---

## ⚖️ Risk-Based Prioritization

As the environment developed, our team worked through controls including:

- Security awareness
- Vulnerability mapping
- System patching
- Stronger Wi-Fi security
- Default credential changes
- Antivirus
- Firewall/security controls
- System hardening
- Logging and analysis

The challenge was not determining whether these controls were useful.

**They were.**

The challenge was deciding:

> **Which action should happen first with the people, budget, and information available right now?**

That changed the way I approached each turn.

Instead of asking:

**"What can we fix?"**

I began asking:

**"What creates the greatest current risk, and which action gives us the greatest risk reduction without introducing unnecessary operational impact?"**

---

## 🔄 My Analyst Decision Pattern

As the simulation progressed, I developed a repeatable decision process:

**Identify → Understand → Prioritize → Remediate → Validate → Hunt**

### Identify
What weakness, alert, or exposure are we dealing with?

### Understand
What asset is affected, and what role does it play in the environment?

### Prioritize
How exploitable is the weakness, how critical is the asset, and what other risks are competing for our resources?

### Remediate
What control can safely reduce the risk?

### Validate
Did the change actually produce the expected result?

### Hunt
Does the available telemetry show evidence that the weakness may already have been exploited?

---

## 🔎 Why This Matters for Threat Hunting

A threat hunter does not begin with a SIEM query.

The hunt begins with understanding the environment well enough to know **what should be happening** so that we can recognize behavior that should not be happening.

This baseline later became increasingly important as the simulation introduced ransomware, unresolved vulnerabilities, IT/OT dependencies, and systems that could not simply be patched immediately.

---

## 💬 Interview Talking Point

> **"The simulator reinforced for me that threat hunting starts before the query. I first need to understand the environment, critical assets, identities, vulnerabilities, expected behavior, and available telemetry. Once I have that baseline, I can form stronger hypotheses and distinguish normal activity from meaningful anomalies."**

---

## 🔑 Key Takeaway

**Visibility is not just a monitoring capability — it is a prerequisite for effective threat hunting.**

Before I can hunt the attacker, I need to understand the environment they are operating in.

---

### Next Case Study
➡️ **02 — Identity & Credential Risk**
