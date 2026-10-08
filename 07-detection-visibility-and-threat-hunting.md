# 07 — Detection, Visibility & Threat Hunting

---

## 🔎 Security Controls Are Only Useful If We Can See What Is Happening

As the simulation progressed, one lesson became increasingly clear:

**Preventing an attack is only part of the job.**

I also need enough visibility to recognize when something suspicious is happening.

That changed the way I looked at controls such as:

- Log collection and analysis
- Endpoint Detection
- Antivirus
- IDS/IPS
- Authentication monitoring
- Network monitoring
- Vulnerability scanning

Each provides a different piece of the security picture.

The question became:

**If an attacker entered this environment today, would we have enough telemetry to recognize their activity?**

---

## 👁️ Visibility Changes What the SOC Can Detect

Early in the simulation, one of my priorities was **Log Collection & Analysis**.

That decision became more important as the environment evolved.

Without adequate logging, suspicious activity may occur without providing analysts enough evidence to investigate it.

Good visibility can help answer questions such as:

- Who authenticated to the system?
- Where did the connection originate?
- What process executed?
- What account performed the action?
- What systems communicated with each other?
- Were privileges changed?
- Was a new service created?
- Did an endpoint contact an unusual destination?
- What happened before and after an alert?

An alert may tell me that something happened.

**Telemetry helps me understand the story around it.**

---

## 🧩 Individual Events Need Context

One of the biggest lessons I have learned from SOC investigations and this simulation is that individual events rarely tell the entire story.

A failed login by itself may be normal.

A PowerShell process may be legitimate.

A new network connection may be expected.

But when those events occur together, the context can change.

For example:

**Repeated failed authentication  
→ Successful authentication  
→ PowerShell execution  
→ Privilege change  
→ Connection to an unfamiliar destination**

Now I am no longer looking at isolated events.

I am looking at a sequence of activity.

That is where investigation begins to move toward threat hunting.

---

## 🧠 From Alert Triage to Threat Hunting

Traditional alert triage often begins with:

**"What triggered this alert?"**

Threat hunting begins with a different question:

**"What suspicious activity might exist that has not triggered an alert yet?"**

That distinction became increasingly important during the simulation.

Instead of relying entirely on alerts, I began thinking about what attacker behavior might look like across the environment.

That means looking for patterns involving:

- Authentication
- Process execution
- Persistence
- Privilege escalation
- Lateral movement
- Network communication
- Credential activity
- Endpoint behavior

The objective is not simply to find another alert.

The objective is to identify **behavior that may indicate an attack story developing across multiple systems.**

---

## 🎯 Vulnerabilities Can Create Hunting Hypotheses

The unresolved vulnerabilities on systems such as **AD-SERVER** and **ENGWS66** created another important connection for me.

If I know a vulnerability exists but cannot immediately patch it, that information can guide proactive hunting.

Instead of only asking:

**"When will this vulnerability be patched?"**

I can also ask:

**"What would exploitation of this vulnerability look like in our telemetry?"**

That creates a hunting hypothesis.

For example:

> If an attacker attempts to exploit this vulnerable asset, I would expect to observe unusual authentication, process execution, privilege activity, network communication, or persistence behavior associated with that system.

Now the vulnerability is not simply a remediation ticket.

It becomes intelligence that can guide monitoring and investigation.

---

## 🛰️ Endpoint Detection Increased Visibility

When vulnerabilities remained on **AD-SERVER** and **ENGWS66** without an available patch, I recommended adding **Endpoint Detection**.

That did not remove the vulnerabilities.

Instead, it improved our ability to observe suspicious activity involving those assets.

This distinction matters.

**Prevention attempts to stop activity.**

**Detection attempts to identify activity.**

**Threat hunting actively searches for activity that may have bypassed existing defenses.**

Together, these capabilities create stronger defense in depth.

---

## 🔗 Hunt the Story, Not the Event

This simulation reinforced a threat-hunting principle that has become central to how I approach investigations:

**Stop hunting events. Hunt the story.**

A single event may not be malicious.

The value comes from connecting activity across:

**User → Endpoint → Process → Network → Destination → Timeline**

For example:

**User account authenticates  
→ Endpoint launches unusual process  
→ Process creates persistence  
→ Host communicates externally  
→ Similar activity appears on another system**

Each event provides context for the next.

The objective is to determine whether those events collectively represent normal activity or attacker behavior.

---

## 🧭 A Simple Hunting Process

My threat-hunting thought process can be summarized as:

**Hypothesis → Data → Search → Correlate → Investigate → Validate → Document**

### 1. Hypothesis

What suspicious behavior am I looking for?

### 2. Data

What telemetry would allow me to observe that behavior?

### 3. Search

Query the available logs, endpoint data, authentication activity, and network telemetry.

### 4. Correlate

Connect related events across users, hosts, processes, IP addresses, and timestamps.

### 5. Investigate

Determine whether the activity is expected, suspicious, or malicious.

### 6. Validate

Confirm the findings using additional evidence.

### 7. Document

Record the hypothesis, evidence, findings, and recommended response.

---

## 🔬 What I Would Hunt For

Depending on the asset and threat scenario, I would investigate indicators such as:

- Repeated authentication failures followed by success
- Authentication from unusual sources
- Unexpected administrative activity
- New or unusual processes
- Suspicious PowerShell execution
- Abnormal parent-child process relationships
- Newly created services
- Scheduled tasks
- Privilege changes
- Unexpected outbound connections
- Communication with unfamiliar destinations
- Lateral movement between systems
- Persistence mechanisms
- Activity occurring outside expected patterns

No single indicator automatically proves compromise.

The goal is to determine whether multiple observations form a meaningful pattern.

---

## 🧠 Threat Hunting Requires Understanding Normal

Threat hunting is not only about knowing what malicious activity looks like.

It also requires understanding what **normal** looks like.

Without a baseline, unusual activity is difficult to identify.

Useful questions include:

- Which users normally access this system?
- What processes normally execute here?
- Which systems normally communicate?
- What destinations are expected?
- What administrative activity is normal?
- When does this system normally operate?

Once normal behavior is understood, deviations become easier to investigate.

---

## 🔄 Detection and Hunting Improve Each Other

Threat hunting should not end when a hunt is completed.

A useful hunt can improve future detection.

The cycle becomes:

**Hunt → Discover → Validate → Build Detection → Monitor → Hunt Again**

If a hunt identifies reliable malicious behavior, that behavior may become the basis for:

- Detection rules
- SIEM queries
- Alert logic
- Endpoint detections
- Monitoring improvements
- Updated investigation procedures

This turns one investigation into a lasting improvement in defensive capability.

---

## 🧭 My Investigation Mindset

By this stage of the simulation, my approach had evolved into:

**Observe → Question → Correlate → Investigate → Validate → Respond**

I do not want to stop at:

**"An alert fired."**

I want to understand:

**What happened?  
What happened before it?  
What happened after it?  
What else is connected to it?  
Is this isolated activity or part of something larger?**

That is the mindset I want to continue developing as I move deeper into threat hunting.

---

## 💬 Interview Talking Point

> "One of the biggest lessons I took from the simulation was the importance of visibility. Security controls can reduce risk, but analysts still need telemetry that allows them to understand what is happening across the environment. I started thinking beyond individual alerts and looking at how authentication, endpoint, process, and network activity could connect into a larger story. When vulnerabilities remained on systems such as AD-SERVER and ENGWS66 without an available patch, I also realized those vulnerabilities could help shape hunting hypotheses. Instead of only waiting for remediation, I could ask what exploitation would look like in the available telemetry and proactively search for that behavior. That helped connect vulnerability management, detection, SOC investigation, and threat hunting for me."

---

## 🔑 Key Takeaway

**Visibility turns activity into evidence. Correlation turns evidence into context. Threat hunting turns that context into questions.**

The SOC cannot investigate what it cannot see.

And threat hunters cannot find the story if they only look at individual events.

**Stop hunting events. Hunt the story.**

---

## Next Case Study

➡️ **08 — Resource Prioritization & SOC Decision-Making**
