# 02 — Identity & Credential Risk

## 🔐 The Challenge

One of the earliest risks we addressed in the simulation was identity security.

The environment contained multiple systems and access points that could become attack paths if credentials were compromised, reused, or left at their defaults. With limited staff and budget, we had to determine which identity controls would reduce the greatest amount of risk early.

Two issues became especially important as the simulation progressed:

- Strengthening authentication with 2FA
- Identifying and changing default credentials

What initially looked like individual configuration tasks became part of a much larger security lesson:

> **Credentials are not just an authentication issue. They can become an attack path.**

A compromised or default credential can provide the foothold an attacker needs to move deeper into an environment.
---

## 🛡️ Priority One — 2FA

One of my first recommendations was to implement **2FA using 2 staff members**.

At that point in the simulation, we had several competing security needs, but authentication represented a foundational risk. If an attacker obtained a valid username and password, those credentials could potentially provide an initial foothold into the environment.

Adding a second authentication factor reduced the value of a compromised password by requiring additional verification before access could be granted.

### Why I Prioritized It

My reasoning was based on reducing an attack path early rather than waiting for evidence of compromise.

A stolen credential can potentially lead to:

**Credential Compromise → Initial Access → Privilege Abuse → Lateral Movement → Persistence**

2FA does not eliminate identity attacks, but it adds another defensive barrier between a compromised password and successful access.

From a threat-hunting perspective, this also reinforced an important distinction:

> **Prevention and detection work together. Stronger authentication can make unauthorized access harder, while authentication telemetry helps us identify attempts to bypass or abuse those controls.**
>
> ---

## 🔑 Priority Two — Default Credentials

As the simulation progressed, default credentials appeared on multiple assets.

This created a different identity risk than a stolen password. An attacker would not necessarily need to steal credentials if a system was still using credentials that were known, predictable, or unchanged from deployment.

That changed how I prioritized remediation.

### Credentials Before Hardening

When both default credentials and system hardening were outstanding, I began prioritizing the credential change first.

My reasoning was simple:

> **Hardening a system does not remove the risk of an attacker authenticating with valid default credentials.**

Changing the credentials directly addressed an immediate access path. Hardening could then reduce the system's broader attack surface.

This led to a practical remediation sequence:

**Change Default Credentials → Harden System → Validate → Monitor**
---

## 🖥️ Applying the Decision to the Environment

The credential risk was not theoretical. As the simulation progressed, several assets were identified as still requiring default credential changes, including:

- PALALTODMZ
- TS-DMZ24
- DMZSECCON
- DMZWIRELESS
- DMZFIREWALL

With limited staff available each turn, I could not address every outstanding control simultaneously.

For example, when PALALTODMZ still required a default credential change, I recommended:

> **Change Default Credentials on PALALTODMZ — 1 person, $0, 1 day**

The important part of that recommendation was not simply completing another task on the board. I was prioritizing an exposed access path.

An asset can have other defensive controls in place and still present significant risk if an attacker can authenticate using credentials that were never changed.

That reinforced the order I began using when credential exposure and hardening competed for the same resources:

**Remove the known access path → Reduce the broader attack surface → Validate the change → Hunt for prior misuse**

This was one of the points where the simulator began shifting my thinking from:

**"What security task should we complete next?"**

to:

**"Which attack path should we remove next?"**
### Threat-Hunting Perspective

Default credentials also create an important hunting question:

**Was the weakness exploited before we fixed it?**

Changing the credentials addresses the current exposure, but it does not tell us whether someone previously used them.

After remediation, I would want to review available authentication and network telemetry for indicators such as:

- Successful logins involving the affected asset
- Unexpected source systems or IP addresses
- Authentication occurring at unusual times
- Access inconsistent with the asset's normal role
- Activity immediately before the credential change
- Follow-on connections to other systems

This was an important shift in my thinking during the simulation:

> **Remediation closes the weakness. Threat hunting asks whether someone already walked through it.**
> ---

## 💬 Interview Talking Point

> "During the simulation, I learned not to treat default credentials as just a configuration issue. I began looking at them as an exposed attack path. I prioritized changing the credential before broader hardening because hardening would not prevent an attacker from authenticating with a valid default credential. After remediation, I would then use authentication and network telemetry to hunt backward for evidence that the credential had already been used."

---

## 🔑 Key Takeaway

**Identity controls are not only preventative controls — they are part of the attack story.**

A credential weakness may begin as a configuration problem, but once an attacker uses that credential, it becomes an investigation.

My job is not only to ask:

**"Did we fix it?"**

but also:

**"Was it exploited before we fixed it?"**

---

### Next Case Study

➡️ **03 — Ransomware Incident Response**
