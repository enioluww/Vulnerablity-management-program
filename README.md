
# Vulnerability Management Program Implementation

In this project, we simulate the implementation of a comprehensive vulnerability management program, from inception to completion.

_**Inception State:**_ the organization has no existing policy or vulnerability management practices in place.

_**Completion State:**_ a formal policy is enacted, stakeholder buy-in is secured, and a full cycle of organization-wide vulnerability remediation is successfully completed.

---

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/cfc5dbcf-3fcb-4a71-9c13-2a49f8bab3e6">

# Technology Utilized
- Tenable (enterprise vulnerability management platform)
- Azure Virtual Machines (Nessus scan engine + scan targets)
- PowerShell & BASH (remediation scripts)

---


# Table of Contents

- [Vulnerability Management Policy Draft Creation](#vulnerability-management-policy-draft-creation)
- [Mock Meeting: Policy Buy-In (Stakeholders)](#step-2-mock-meeting-policy-buy-in-stakeholders)
- [Policy Finalization and Senior Leadership Sign-Off](#step-3-policy-finalization-and-senior-leadership-sign-off)
- [Mock Meeting: Initial Scan Permission (Server Team)](#step-4-mock-meeting-initial-scan-permission-server-team)
- [Initial Scan of Server Team Assets](#step-5-initial-scan-of-server-team-assets)
- [Vulnerability Assessment and Prioritization](#step-6-vulnerability-assessment-and-prioritization)
- [Distributing Remediations to Remediation Teams](#step-7-distributing-remediations-to-remediation-teams)
- [Mock Meeting: Post-Initial Discovery Scan (Server Team)](#step-8-mock-meeting-post-initial-discovery-scan-server-team)
- [Mock CAB Meeting: Implementing Remediations](#step-9-mock-cab-meeting-implementing-remediations)
- [Remediation Round 1: Outdated Wireshark Removal](#remediation-round-1-outdated-wireshark-removal)
- [Remediation Round 2: Insecure Protocols & Ciphers](#remediation-round-2-insecure-protocols--ciphers)
- [Remediation Round 3: Guest Account Group Membership](#remediation-round-3-guest-account-group-membership)
- [First Cycle Remediation Effort Summary](#first-cycle-remediation-effort-summary)

---

### Vulnerability Management Policy Draft Creation

This phase focuses on drafting a Vulnerability Management Policy as a starting point for stakeholder engagement. The initial draft outlines scope, responsibilities, and remediation timelines, and may be adjusted based on feedback from relevant departments to ensure practical implementation before final approval by upper management.  
[Draft Policy](https://docs.google.com/document/d/1CLSWm1_9JL1oUqgyNNwtPXW6FzXJ7ddVnSAUQTyqC8I/edit?usp=drive_link)

---

### Step 2) Mock Meeting: Policy Buy-In (Stakeholders)

In this phase, a meeting with the server team introduces the draft Vulnerability Management Policy and assesses their capability to meet remediation timelines. Feedback leads to adjustments, like extending the critical remediation window from 48 hours to one week, ensuring collaborative implementation.


# 💬 Policy Discussion: Remediation Timelines

> **Context:**  
> A brief professional conversation between **Josh** and **Jimmy** discussing adjustments to a new vulnerability remediation policy.  
> This dialogue demonstrates collaborative problem-solving, policy negotiation, and clear communication within an IT security environment.

---

## 🗣️ Dialogue

**Josh:**  
Hey, good morning, Jimmy. How’s everything been lately? I know everyone’s been pretty busy these last few weeks.  

**Jimmy:**  
Good morning, Josh. Yeah, it’s been a bit hectic, but we’re hanging in there — thanks for asking. I had a chance to read through the policy draft, and overall it makes sense. However, with our current staffing, we can’t meet the aggressive remediation timelines — especially the 48-hour window for critical vulnerabilities.  

**Josh:**  
Yeah, I totally understand. It is a bit aggressive, especially to start. Maybe we can extend the critical window to one week for now? That might be a good compromise, and we can reserve the 48-hour response for truly severe zero-day vulnerabilities.  

**Jimmy:**  
That sounds reasonable. We appreciate the flexibility. Could we also have a bit of leeway in the beginning as we get used to the remediation and patching process — maybe for the first few months?  

**Josh:**  
Absolutely. After the policy is finalized, we’ll officially start the program, but we’re planning to give all departments about six months to adjust and get comfortable with the new process. Does that sound fair?  

**Jimmy:**  
That’s perfect, Josh. We’ll do our best. I really appreciate you including us in the decision-making process — it helps us feel like we’re part of the solution.  

**Josh:**  
Of course. We’re all in this together. Thanks for working with us.  

**Jimmy:**  
No problem — and thanks for keeping it short!  

**Josh:**  
Yeah, those are my favorite kinds of meetings. Take care!  

**Jimmy:**  
See you later.  

---

## 🧩 Key Takeaways

- 🤝 **Collaboration:** Both parties worked together to find a realistic solution.  
- ⏱️ **Practical Adjustment:** Extended remediation timelines to match staffing capacity.  
- 🧠 **Strategic Flexibility:** Introduced phased implementation and exception handling.  
- 💬 **Positive Communication:** Demonstrated mutual respect and teamwork in policy planning.  

---

### 🧾 Summary

This discussion reflects real-world communication in cybersecurity and IT policy environments — balancing **security requirements** with **operational feasibility**, while maintaining **constructive dialogue** between technical and management teams.


---

### Step 3) Policy Finalization and Senior Leadership Sign-Off

After gathering feedback from the server team, the policy is revised, addressing aggressive remediation timelines. With final approval from upper management, the policy now guides the program, ensuring compliance and reference for pushback resolution.  
[Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link)
<div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/9afcdbc1-0493-4af2-9287-1cb9b8f59b40" alt="image" width="400">
</div>

---

### Step 4) Mock Meeting: Initial Scan Permission (Server Team)

The team collaborates with the server team to initiate scheduled credential scans. A compromise is reached to scan a single server first, monitoring resource impact, and using just-in-time Active Directory credentials for secure, controlled access.  

# 🧪 Vulnerability Scanning Discussion

> **Context:**  
> A conversation between **Josh** and **Jimmy** about initiating scheduled credentialed vulnerability scans following the implementation of a new vulnerability management policy.  
> This dialogue demonstrates security planning, risk communication, and operational collaboration in an enterprise IT setting.

---

## 🗣️ Dialogue

**Josh:**  
Morning, Jimmy. I heard you’re ready to conduct some scans.  

**Jimmy:**  
Yep! Now that our vulnerability management policy is in place, I wanted to start scheduling some credentialed scans of your environment.  

**Josh:**  
Sounds good to me. What’s involved, and how can we help?  

**Jimmy:**  
We’re planning to schedule weekly scans of the server infrastructure. We estimate it’ll take about 4–6 hours to scan all 200 assets.  
We’ll need you to provide some administrative credentials so the scan engine can remotely log into the targets for a deeper assessment.  

**Josh:**  
Whoa, hold on — what does scanning actually entail? I’m a bit worried about resource utilization.  
Also, you want admin credentials to all 200 machines? That doesn’t sound safe.  

**Jimmy:**  
Those are valid concerns. The scan engine basically sends different types of traffic to the servers to check for the presence of known vulnerabilities.  
This includes looking into the registry, identifying outdated software, and checking for insecure protocols or cipher suites — that kind of thing.  
That’s why credentials are needed, to give the scan deeper visibility.  

**Josh:**  
I see. As long as it doesn’t bring the servers offline, we should be okay.  

**Jimmy:**  
Absolutely. Let’s start small — we can scan a single server first and monitor resource utilization.  

**Josh:**  
Not a bad idea.  

**Jimmy:**  
Also, for credentials, could you set up something in Active Directory for us? Maybe dedicated AD credentials that remain disabled until the scan begins, then enabled during the scan, and disabled again after — kind of a just-in-time access approach.  

**Josh:**  
That sounds good. I’ll ask Susan to start on the automation for account provisioning.  

**Jimmy:**  
Awesome. Talk soon!  

**Josh:**  
Sounds good. I’ll get back to you once the credentials are set up. See you later.  

**Jimmy:**  
See you later.  

---

## 🧩 Key Takeaways

- 🧠 **Security Awareness:** Addressed concerns about administrative credentials and resource impact.  
- 🔐 **Controlled Access:** Implemented a just-in-time Active Directory account strategy.  
- 🕒 **Incremental Rollout:** Began with limited-scope testing before full deployment.  
- 🤝 **Collaboration:** Demonstrated clear communication between teams to ensure safe and effective vulnerability management.  

---

### 🧾 Summary

This discussion highlights best practices in **vulnerability management** — including credential handling, operational transparency, and phased implementation.  
It shows how technical teams can align security processes with system reliability and stakeholder trust.

---

### Step 5) Initial Scan of Server Team Assets

In this phase, an insecure Windows Server is provisioned to simulate the server team's environment. After creating vulnerabilities, an authenticated scan is performed, and the results are exported for future remediation steps.  

<img width="906" height="813" alt="Screenshot 2025-10-04 at 4 18 49 AM" src="https://github.com/user-attachments/assets/402894a5-676e-492e-83ed-4f03a7a34ccf" />
[Scan 1 - Initial Scan](https://drive.google.com/file/d/1RBPVj_azKJMwmRZ8QILlb4hxIjQU3wQ7/view?usp=drive_link)






---

### Step 6) Vulnerability Assessment and Prioritization

We assessed vulnerabilities and established a remediation prioritization strategy based on ease of remediation and impact. The following priorities were set:

1. Third Party Software Removal (Wireshark)
2. Windows OS Secure Configuration (Protocols & Ciphers)
3. Windows OS Secure Configuration (Guest Account Group Membership)
4. Windows OS Updates

---

### Step 7) Distributing Remediations to Remediation Teams

The server team received remediation scripts and scan reports to address key vulnerabilities. This streamlined their efforts and prepared them for a follow-up review.  

<img width="635" alt="image" src="https://github.com/user-attachments/assets/bbf9478f-e1d1-4898-846e-b510ec8c6f72">

[Remediation Email](https://github.com/joshmadakor1/lognpacific-public/blob/main/misc/remediation-email.md)

---

### Step 8) Mock Meeting: Post-Initial Discovery Scan (Server Team)

The server team reviewed vulnerability scan results, identifying outdated software, insecure accounts, and deprecated protocols. The remediation packages were prepared for submission to the Change Control Board (CAB). 

# 🧰 Vulnerability Findings & Remediation Discussion

> **Context:**  
> A conversation between **Josh** and **Jimmy** following a vulnerability scan.  
> They review scan performance, discuss findings, and plan remediation strategies — emphasizing collaboration, technical insight, and responsible vulnerability management.

---

## 🗣️ Dialogue

**Josh:**  
Morning, Jimmy. How are you doing?  

**Jimmy:**  
Not bad for a Monday. And yourself?  

**Josh:**  
Still alive, so I can’t complain.  
Before we get into the vulnerabilities, how did the actual scan go on your end? Any outages or performance issues?  

**Jimmy:**  
The scan went well. We were monitoring everything closely, and aside from all the open connections, we wouldn’t have even known a scan was happening.  

**Josh:**  
That’s good news — just what I expected. We’ll keep monitoring, but I don’t foresee any resource utilization issues.  
Mind if I dive into the vulnerability findings?  

**Jimmy:**  
Absolutely, go ahead.  

**Josh:**  
Cool. I’ll share my screen really quick.  
So, the majority of these vulnerabilities are from **Wireshark** being installed — it’s just very out of date.  
One interesting thing I found: the **local guest account** on several servers is actually part of the **Administrators group**, which shouldn’t be the case.  

Some other vulnerabilities might be automatically resolved by **Windows Update**, like this **Microsoft Edge (Chromium)** one.  
We can also ignore the **self-signed certificate** alert — that’s expected.  

The main issues we should focus on are:  
- ⚙️ **Deprecated cipher suites (medium-strength)**  
- ⚙️ **Deprecated TLS protocols (1.0 and 1.1)**  
- ⚙️ **Outdated Wireshark installations**  
- ⚙️ **Guest account with admin privileges**  

**Jimmy:**  
Very interesting. The good news is that most of our servers likely have the same vulnerabilities, which should make remediation easier across the board.  

**Josh:**  
Exactly — a uniform rollout helps. Do you foresee any problems fixing the cipher suites or disabling those insecure protocols?  

**Jimmy:**  
Highly doubt it. We’ll run it through the next **Change Control Board**.  
Uninstalling Wireshark and fixing the guest account won’t be an issue either — those shouldn’t be on production servers anyway.  
I’ll coordinate with our **CIS admins** about that.  

**Josh:**  
Perfect. I’ll start building **remediation packages** to streamline the fixes.  

**Jimmy:**  
Sounds great. Oh — do you already have something in place to handle Windows Update-related vulnerabilities?  

**Josh:**  
Yes, we have **Patch Management** in place. Updates should be applied automatically by next week.  

**Jimmy:**  
Excellent. I’ll get started on researching the best approach to remediate these findings and follow up before the next Change Control Board.  

**Josh:**  
Sounds good. Talk to you soon.  

**Jimmy:**  
Cool, talk to you soon.  

---

## 🧩 Key Takeaways

- 🧠 **Technical Insight:** Identified specific vulnerabilities and prioritized actionable ones.  
- 🧰 **Operational Efficiency:** Streamlined remediation through centralized patching and automation.  
- 🔐 **Security Hygiene:** Addressed privilege escalation risks and outdated software.  
- 🤝 **Collaboration:** Coordinated across teams for remediation and governance approval.  

---

### 🧾 Summary

This discussion demonstrates **effective vulnerability management communication**, combining **technical precision** with **cross-team coordination**.  
It highlights real-world cybersecurity operations — from vulnerability analysis to remediation planning — with a focus on collaboration, transparency, and continuous improvement.


---

### Step 9) Mock CAB Meeting: Implementing Remediations

The Change Control Board (CAB) reviewed and approved the plan to remove insecure protocols and cipher suites. The plan included a rollback script and a tiered deployment approach.  

# 🛡️ Vulnerability Remediation Planning – CAP Meeting Discussion

> **Context:**  
> A conversation during a **Change Advisory Panel (CAP) meeting** between the **Risk** and **Infrastructure** teams.  
> The discussion focuses on the **removal of insecure protocols and cipher suites**, implementation strategy, rollback planning, and automation through PowerShell scripts.  
> This scenario highlights structured change management, security automation, and technical communication.

---

## 🗣️ Dialogue

**Facilitator:**  
Okay, next up on the list are a couple of vulnerability remediations for the server team.  
Number one — removal of **insecure protocols**, and number two — removal of **insecure cipher suites**.  

It looks like **Josh** from the **Risk Department** is working in conjunction with **Jimmy** from **Infrastructure** on this.  
Jimmy, do you want to walk us through the technical aspects of the change being implemented?  

**Jimmy:**  
Normally I would, but do you mind giving this one to Josh?  
He actually built the solution for us — we’re still getting used to the process.  

**Josh:**  
Yeah, I can explain this one.  

Basically, **insecure cipher suites and protocols** mean that the system is still capable of negotiating or using deprecated algorithms.  
If it connects to a server that only supports those outdated protocols, it may still use them — creating a security risk.  

These settings are controlled via the **Windows Registry**, and the fix is fairly simple.  
We wrote a **PowerShell script** that goes through and disables all insecure protocols and ciphers, then enables the ones that are considered modern and secure by today’s standards.  

**Facilitator:**  
That sounds good — but what if something goes wrong?  
Do we have a rollback plan in place? Did you even think about that?  

**Josh:**  
Yes, absolutely.  
First, we’re doing a **tiered deployment** — starting with a **pilot group**, then **pre-production**, and finally **production**.  

On top of that, we’ve built an **automated rollback script** for each remediation.  
If any issues arise, the script will restore the original protocol and cipher configurations.  

**Facilitator:**  
That’s good to hear. Since these are registry changes, I’m not too concerned.  

**Josh:**  
Exactly — simple, contained, and reversible.  

**Facilitator:**  
Any more questions from anyone?  

*(silence)*  

Alright, that wraps things up for this week’s CAP meeting.  
See you all next week!  

**All:**  
See you later.  

---

## 🧩 Key Takeaways

- ⚙️ **Security Hardening:** Removed deprecated SSL/TLS protocols and weak cipher suites.  
- 💻 **Automation:** Implemented PowerShell scripts for consistent remediation and rollback.  
- 🧪 **Controlled Deployment:** Used a phased rollout — pilot → pre-production → production.  
- 🔄 **Rollback Strategy:** Automated reversion scripts ensure minimal operational risk.  
- 🤝 **Cross-Team Collaboration:** Risk and Infrastructure teams coordinated on design and testing.  

---

### 🧾 Summary

This discussion showcases how cybersecurity and infrastructure teams collaborate during **change management**.  
It demonstrates the practical application of **secure configuration**, **automation**, and **rollback planning** — all key elements in maintaining a resilient enterprise environment.

---
### Step 10 ) Remediation Effort

#### Remediation Round 1: Outdated Wireshark Removal

The server team used a PowerShell script to remove outdated Wireshark. A follow-up scan confirmed successful remediation.  
[Wireshark Removal Script](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/remediation-wireshark-uninstall.ps1)  

<img width="1544" height="1478" alt="image" src="https://github.com/user-attachments/assets/399416dd-929d-44bc-95ba-848b9128c74e" />

[Scan 2 - Third Party Software Removal](https://drive.google.com/file/d/1UiwPPTtuSZKk02hiMyXf31pXUIeC5EWt/view?usp=drive_link)


#### Remediation Round 2: Insecure Protocols & Ciphers

The server team used PowerShell scripts to remediate insecure protocols and cipher suites. A follow-up scan verified successful remediation, and the results were saved for reference.  
[PowerShell: Insecure Protocols Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-protocols.ps1)
[PowerShell: Insecure Ciphers Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-cipher-suites.ps1)

<img width="1558" height="850" alt="image" src="https://github.com/user-attachments/assets/0f03abf1-edc2-4eb0-865f-b90ac96c46a2" />

[Scan 3 - Ciphersuites and Protocols](https://drive.google.com/file/d/1Qc6-ezQvwReCGUZNtnva0kCZo_-zW-Sm/view?usp=drive_link)


#### Remediation Round 3: Guest Account Group Membership

The server team removed the guest account from the administrator group. A new scan confirmed remediation, and the results were exported for comparison.
Windows updates were re-enabled and applied until the system was fully up to date. A final scan verified the changes  
[PowerShell: Guest Account Group Membership Remediation](https://github.com/joshmadakor1/lognpacific-public/blob/main/automation/toggle-guest-local-administrators.ps1)  

<img width="1558" height="774" alt="image" src="https://github.com/user-attachments/assets/410d7cb9-45cb-4242-bf6e-2a3b57974d9e" />


[Scan 4 - Post Windows Updates and  Guest Account Group Removal](https://drive.google.com/file/d/1jVgikjfrV1YjOcL3QRT_oUB0Y82w22V7/view?usp=drive_link)




---

### First Cycle Remediation Effort Summary

The remediation process reduced total vulnerabilities by 80%, from 30 to 6. Critical vulnerabilities were resolved by the second scan (100%), and high vulnerabilities dropped by 90%. Mediums were reduced by 76%. In an actual production environment, asset criticality would further guide future remediation efforts.  

<img width="1206" height="754" alt="image" src="https://github.com/user-attachments/assets/5cd9b2da-e38c-4017-be79-38cdcc6871dc" />


[Remediation Data](https://docs.google.com/spreadsheets/d/1FTtFfZYmFsNLU6pm8nTzsKyKE-d2ftXzX_DPwcnFNfA/edit?gid=0#gid=0)

---

### On-going Vulnerability Management (Maintenance Mode)

After completing the initial remediation cycle, the vulnerability management program transitions into **Maintenance Mode**. This phase ensures that vulnerabilities continue to be managed proactively, keeping systems secure over time. Regular scans, continuous monitoring, and timely remediation are crucial components of this phase. (See [Finalized Policy](https://docs.google.com/document/d/1rvueLX_71pOR8ldN9zVW9r_zLzDQxVsnSUtNar8ftdg/edit?usp=drive_link) for scanning and remediation cadence requirements.)

Key activities in Maintenance Mode include:
- **Scheduled Vulnerability Scans**: Perform regular scans (e.g., weekly or monthly) to detect new vulnerabilities as systems evolve.
- **Patch Management**: Continuously apply security patches and updates, ensuring no critical vulnerabilities remain unpatched.
- **Remediation Follow-ups**: Address newly identified vulnerabilities promptly, prioritizing based on risk and impact.
- **Policy Review and Updates**: Periodically review the Vulnerability Management Policy to ensure it aligns with the latest security best practices and organizational needs.
- **Audit and Compliance**: Conduct internal audits to ensure compliance with the vulnerability management policy and external regulations.
- **Ongoing Communication with Stakeholders**: Maintain open communication with teams responsible for remediation, ensuring efficient coordination.

By maintaining an active vulnerability management process, organizations can stay ahead of emerging threats and ensure long-term security resilience.
