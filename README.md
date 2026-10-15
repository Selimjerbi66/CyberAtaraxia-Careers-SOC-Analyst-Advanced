<div align="center">
  <img src="https://github.com/Selimjerbi66/CyberAtaraxia-Suite/blob/main/cyberataraxia_new_logo.png?raw=true" width="180" alt="CyberAtaraxia Logo"/>
  <h1>CyberAtaraxia Careers — SOC Analyst Advanced</h1>

  <p>
    A hands-on, full-scale enterprise lab to go from SOC fundamentals to advanced detection engineering, Active Directory defense, purple teaming and incident response — part of the <strong>CyberAtaraxia Suite</strong> by <strong>Selim JERBI</strong>
  </p>
  <p>
    <img src="https://img.shields.io/badge/Status-In%20Development-blue?style=for-the-badge" />
    <img src="https://img.shields.io/badge/License-Open%20Source-green?style=for-the-badge" />
    <img src="https://img.shields.io/badge/Cost-Free%20%26%20Open%20Source%20Tools-success?style=for-the-badge" />
    <a href="https://github.com/Selimjerbi66">
      <img src="https://img.shields.io/badge/Made%20by-Selim%20JERBI-blueviolet?style=for-the-badge" />
    </a>
  </p>
  <p>
    🇬🇧 <a href="README.md">English</a> &nbsp;|&nbsp; 🇫🇷 <a href="README_FR.md">Français</a>
  </p>
</div>

---

## 🧭 About This Career Path

**CyberAtaraxia Careers** is a line within the CyberAtaraxia Suite: guided, hands-on **career paths** rather than single tools — each one designed to produce a demonstrable, portfolio-ready skillset using free and open-source resources.

**SOC Analyst Advanced** is the follow-up to the *SOC Analyst* path. Where the first path uses lightweight, file-based detection on 3 VMs, this one builds what a real SOC actually runs: a **virtualized enterprise information system** with an Active Directory domain, a centralized **SIEM/XDR (Wazuh)**, a **network security monitoring platform (Security Onion with Suricata and Zeek)**, and a dedicated attacker machine. You then attack your own environment in a controlled way, observe what the SOC sees, what it misses, and **improve the defenses until the gaps are closed**.

It's not a course you read — it's an environment you *build, attack, defend and measure*.

No production systems are touched. Every offensive operation stays inside an isolated virtual lab.

---

## 🎯 Main Goal

Take you from SOC fundamentals to **hands-on, practical experience across the full defensive lifecycle of an enterprise environment** — not just reading about SIEM, MITRE ATT&CK, Active Directory attacks and incident response, but running each one end to end against real (safely simulated) attacks:

> build → secure → monitor → attack → detect → investigate → respond → improve → replay

Everything is organized around **one continuous storyline and one iterative loop (Purple Team)**: every attack scenario is confronted with the detection stack, every gap becomes a new detection rule or hardening measure, and every scenario is replayed to **prove** the improvement.

---

## 🏁 What You'll Walk Away With

| # | Deliverable | What it proves |
|---|---|---|
| 1 | A working **virtualized enterprise lab** (AD domain, Windows server and workstation, Linux, Kali attacker) | You can design and deploy a realistic, segmented and documented environment |
| 2 | A functional **Active Directory** (OUs, users, groups, privileges, DNS) with hardening and deliberate, documented weaknesses | You understand AD from both the admin and the attacker point of view |
| 3 | A configured **SOC platform**: Wazuh + Security Onion (Suricata, Zeek) with Windows and Linux log sources | You can centralize, correlate and exploit security events |
| 4 | Custom **detection rules** (Wazuh, Suricata, Zeek) mapped to MITRE ATT&CK | You can go from "no visibility" to "detected and mapped" |
| 5 | Documented **controlled attack scenarios** (recon, enumeration, AD attacks, privilege escalation, lateral movement) | You can run realistic attacks with discipline and scope control |
| 6 | A **MITRE ATT&CK ↔ observable traces ↔ detection ↔ MITRE D3FEND** mapping and a detection coverage assessment | You can measure defense instead of assuming it |
| 7 | **Investigation reports** and **incident response procedures** | You can run the full IR lifecycle and communicate it |
| 8 | A **technical audit** and a **risk analysis** inspired by EBIOS Risk Manager, with prioritized recommendations | You can assess a system and drive improvements |
| 9 | A **GitHub repo** with configs, rules, scenarios, scripts and reports | A concrete artifact to show in interviews |

This isn't "I installed some tools" — it's a live, measurable lab and a documented before/after improvement story.

---

## 🧰 Hardware & Budget

| Item | Needed? | Notes |
|---|---|---|
| **PC / host machine** | Required | Recommended: **32 GB RAM**, 8+ CPU threads, **~500 GB free SSD**. 16 GB is possible only with the *staged profiles* below (not everything runs at once). |
| **Hypervisor** | Required | **VMware Workstation** (Pro or Player depending on your license). |
| **Router / physical switch** | Not needed | Everything is virtual. |
| **Software** | Free / evaluation | Windows Server and Windows 11 use official Microsoft evaluation ISOs. Everything else is open source. |

> 💡 The lab is designed so that **not all VMs need to run simultaneously**. See *Run Profiles*.

---

## 🗺️ Lab Architecture

| VM | Role | Main components |
|---|---|---|
| **Windows Server 2022** | Domain Controller | AD DS, DNS, users/groups/GPO management |
| **Windows 11** | Domain workstation | Wazuh agent, Sysmon, advanced audit policies, PowerShell logging |
| **Ubuntu Server LTS** | SIEM/XDR | Wazuh manager, indexer, dashboard |
| **Security Onion** | Network security monitoring | Suricata (IDS), Zeek (network metadata), PCAP, analysis console |
| **Kali Linux** | Attacker | Recon, enumeration, vulnerability analysis, AD attacks |

```
                       ┌───────────────────────────┐
                       │   Kali Linux (attacker)   │
                       └─────────────┬─────────────┘
                                     │  attack network
   ┌─────────────────────────────────┴──────────────────────────────┐
   │                    Corporate LAN (virtual switch)               │
   │   ┌────────────────────┐              ┌─────────────────────┐  │
   │   │ Windows Server 2022│              │     Windows 11      │  │
   │   │   AD DS + DNS      │◄────────────►│  domain workstation │  │
   │   └─────────┬──────────┘              └──────────┬──────────┘  │
   └─────────────┼──────────────────────────┬─────────┼─────────────┘
                 │ Wazuh agents (logs)      │ mirrored traffic
                 ▼                          ▼
        ┌─────────────────┐        ┌─────────────────────┐
        │ Ubuntu + Wazuh  │        │    Security Onion   │
        │ SIEM / XDR      │        │  Suricata + Zeek    │
        └─────────────────┘        └─────────────────────┘
                   (management / SOC network)
```

**Network principles**

- A dedicated **lab network** with static IPs and a documented addressing plan (corporate LAN, attack network, management/SOC network).
- Security Onion's sniffing interface sits on a segment that **sees the monitored traffic** (promiscuous mode / mirroring on the virtual switch).
- The lab is **isolated** from your real network. Internet is only used temporarily for updates and downloads.
- **Clean snapshots** at every stable step (after AD, after client join, before hardening, before each attack campaign).

### ⚙️ Run Profiles

| Profile | VMs running | Use case |
|---|---|---|
| **Foundation** | Windows Server + Windows 11 | AD build, hardening, GPO |
| **Endpoint SOC** | + Ubuntu/Wazuh | Host-based detection, rules, dashboards |
| **Network SOC** | + Security Onion | Suricata/Zeek tuning, PCAP analysis |
| **Full Purple** | + Kali (all VMs) | Attack scenarios and replay |

---

## 🛠️ Tools Used

- **Hypervisor:** VMware Workstation
- **Identity & infrastructure:** Windows Server 2022 (AD DS, DNS, GPO), Windows 11
- **SIEM / XDR / HIDS:** **Wazuh** (manager, indexer, dashboard, agents)
- **Endpoint visibility:** Windows advanced audit policy, PowerShell Script Block Logging, **Sysmon** (community config), auditd (Linux)
- **Network security monitoring:** **Security Onion**, **Suricata**, **Zeek**, PCAP analysis, Wireshark
- **Offensive tooling (lab only):** Kali Linux — Nmap, enumeration tools, BloodHound/SharpHound, Impacket, NetExec/CrackMapExec, Responder, Metasploit, etc.
- **Frameworks:** **MITRE ATT&CK** (+ Navigator), **MITRE D3FEND**, EBIOS Risk Manager (inspired approach)
- **Attack simulation (optional):** Atomic Red Team
- **Documentation:** Markdown in the repo, draw.io / diagrams.net, Obsidian
- **Optional extras:** Docker (and Kubernetes exploration), Python/PowerShell/Bash scripting, AI-assisted SOC use cases

---

## 🔄 Methodology — The Iterative Loop

```
 1 Design & deploy ─► 2 Secure & configure ─► 3 Collect logs & monitor
        ▲                                                │
        │                                                ▼
 10 Document & recommend                       4 Run controlled attacks
        ▲                                                │
 9 Replay scenarios ◄─ 8 Fix gaps ◄─ 7 Map ATT&CK/D3FEND ◄─ 5 Observe traces ◄─ 6 Detect, investigate, respond
```

Each scenario follows the same pattern: **attack → observable traces → alert (or blind spot) → investigation → mapping → improved rule/hardening → replay → measured result.**

---

## 📅 The Roadmap

<details>
<summary><strong>Phase 1 — Design & Build the Lab (October)</strong></summary>

- Define the detailed requirements, scope, deliverables and "definition of done" for each one.
- Design the architecture, addressing plan, naming convention, log flows and snapshot strategy.
- Install and configure VMware and the virtual networks.
- Create and install the Windows Server 2022 and Windows 11 VMs.
- Deploy **Active Directory** (domain, DNS, OUs, users, groups, service accounts) and join the workstation to the domain.
- Initial **Wazuh** installation and agent deployment.
- First hardening and logging measures (audit policy, PowerShell logging, Sysmon).

**Expected result:** a documented, stable base infrastructure, ready to be monitored.
</details>

<details>
<summary><strong>Phase 2 — Deploy the SOC & First Detections (November)</strong></summary>

- Finalize the Wazuh configuration.
- Deploy **Security Onion** with **Suricata** and **Zeek**.
- Integrate Windows and Linux log sources, verify collection end to end.
- Create and test the first detection rules (Wazuh decoders/rules, Suricata rules).
- Run simple scenarios and start the initial **MITRE ATT&CK** mapping.
- Build dashboards and alert-triage routines.

**Expected result:** a functional SOC that collects events and detects several suspicious activities.
</details>

<details>
<summary><strong>Phase 3 — Attack Scenarios & Purple Team (December)</strong></summary>

- Set up Kali Linux and prepare the offensive scenarios.
- Reconnaissance and enumeration of the environment.
- Security testing on Windows, Linux and **Active Directory** (Kerberoasting, AS-REP roasting, password attacks, credential access, etc.).
- Privilege escalation and lateral movement where the context allows it.
- Observe and analyze host and network traces; correlate system and network events.
- Map each technique to **MITRE D3FEND** countermeasures.
- Improve rules, replay scenarios, measure progress.

**Expected result:** documented scenarios that evaluate the SOC and lead to concrete improvements.
</details>

<details>
<summary><strong>Phase 4 — Audit, Risk & Automation (late December – early January)</strong></summary>

- Technical audit of the environment (configuration, log availability, detection capability).
- Identify weaknesses and detection gaps.
- Risk analysis inspired by **EBIOS Risk Manager** (assets, threats, risk scenarios, treatment).
- Prioritized recommendations.
- Automation scripts where they add real value.
- *Optional:* Docker / Kubernetes exploration and AI use-case study.

**Expected result:** a structured technical assessment, a risk analysis and prioritized improvement recommendations.
</details>

<details>
<summary><strong>Phase 5 — Final Validation & Presentation (January)</strong></summary>

- Finalize configurations and scenarios, verify the whole environment.
- Replay all attack scenarios and evaluate the improvements.
- Consolidate the ATT&CK / D3FEND mapping and the coverage matrix.
- Finalize investigation reports, procedures and documentation.
- Write the final report, prepare the presentation and the live technical demonstration.

**Expected result:** a documented lab, evaluated results, and a demo showing the architecture, scenarios, detection capabilities and improvements.
</details>

---

## 🧩 Workstreams in Detail

### 🏗️ 1. Architecture & Environment
Network and system design, identification of components and flows to monitor, logging/collection/detection requirements, documentation of every technical choice.

### 🔒 2. System Hardening
Windows and Linux configuration, hardening measures, accounts/rights/policies, logging mechanisms, and verification that the protections actually work.

### 🛡️ 3. SOC Platform
Wazuh and Security Onion deployment, Windows and Linux log integration, Suricata/Zeek network supervision, event centralization and correlation, custom rules, dashboards and alerts.

### 🔎 4. Threat Detection
Identifying security-relevant events, detecting suspicious behavior on hosts and network, separating legitimate from malicious activity, **system ↔ network correlation**, and **reducing false positives**.

### 🧭 5. MITRE ATT&CK & D3FEND
Mapping scenarios to tactics/techniques, identifying observable traces and indicators, associating D3FEND countermeasures, assessing detection coverage, and documenting gaps.

### ⚔️ 6. Controlled Pentesting
Recon and enumeration, controlled exploitation of lab vulnerabilities, Windows/Linux scenarios, AD scenarios, privilege escalation and lateral movement, observation of offensive traces and evaluation of SOC detection.

### 🏰 7. Active Directory Security
Domain deployment, users/groups/privileges, event log analysis, AD attack scenarios, and implementation and evaluation of detection and hardening measures.

### 🟣 8. Purple Team
Confront attacks with detections, analyze traces and alerts, find undetected or poorly covered techniques, improve rules and defenses, replay scenarios to measure progress.

### 🚨 9. Investigation & Incident Response
Alert qualification, chronological reconstruction, system and network trace correlation, identification of affected systems and accounts, containment / eradication / remediation proposals, and investigation reports and response procedures.

### 📋 10. Technical Audit
System and security configuration review, log collection and availability checks, assessment of monitoring and detection capabilities, vulnerability identification and recommendations.

### ⚖️ 11. Risk Analysis
Asset identification, threats/vulnerabilities/risk scenarios, EBIOS Risk Manager-inspired assessment, treatment measures and prioritization.

### 🧪 12. Secondary Objectives *(only if time and resources allow)*
- **Docker / cloud-native:** containerization basics, complementary services, container security risks, monitoring and detection in that environment (Kubernetes as exploration only).
- **Automation:** scripts for collection, analysis and repetitive tasks, structured and documented.
- **Artificial intelligence:** exploratory study of SOC use cases and, possibly, a limited prototype.

---

## 📊 Detection Coverage Matrix (Template)

The core evidence of the project is a matrix linking each scenario to what was observed and defended:

| ATT&CK Tactic | Technique | Scenario | Observable traces | Detection (rule) | D3FEND countermeasure | Status (1st run) | Status (replay) |
|---|---|---|---|---|---|---|---|
| Credential Access | T1558.003 Kerberoasting | AD scenario | Event 4769 (RC4 ticket), Zeek Kerberos logs | Wazuh custom rule | Credential hardening | ❌ / ⚠️ / ✅ | ✅ |
| Discovery | T1046 Network Service Discovery | Recon | Connection bursts, Suricata scan alerts | Suricata / Zeek | Network traffic analysis | ✅ | ✅ |

*(Illustrative rows — the full matrix is built throughout the project.)*

---

## 📁 Repository Structure

```
/docs            # requirements, architecture decisions, journal
/architecture    # diagrams, addressing plan, network flows
/configs         # system, Wazuh, Security Onion, Sysmon configs
/scenarios       # documented attack scenarios
/detections      # Wazuh, Suricata, Zeek rules + ATT&CK/D3FEND mapping
/reports         # investigation reports, audit, risk analysis
/scripts         # automation scripts
```

---

## ✅ Success Criteria

- Coherent, high-quality architecture
- Stable, functioning virtualized environment
- Relevant hardening measures
- Quality of log collection and centralization
- Relevant detection mechanisms
- Realistic, well-controlled attack scenarios
- Quality of investigations and response procedures
- Ability to identify gaps and improve defenses
- Quality of the ATT&CK / D3FEND mapping
- Relevance of the audit and risk analysis
- Quality of documentation, report and demonstration

---

## ⚠️ Ethics & Legal Notice

All offensive operations are **strictly limited to the isolated virtual lab** built in this project. Never run these techniques against systems you don't own or have explicit written authorization to test. This repository is for **educational and defensive purposes only**.

---

## 🚧 Note on Scope

Cloud security monitoring (AWS/Azure/GCP), full SOAR automation and production-scale SIEM operations are out of scope. Docker, Kubernetes, automation and AI are **secondary or optional** objectives, pursued only after the core objectives are met.

---

## 👤 About the Developer

- 🎓 Network Engineering student at **Polytech Dijon**, specializing in Cybersecurity
- 🔵 Blue Teamer | ICT Auditor | Network Administrator
- 🏢 Cybersecurity Intern at **Axem Belgium**
- 🌱 Currently pursuing **Blue Team L1 · ISO 27001/2022 · CCNA**

<p align="center">
  <a href="https://linkedin.com/in/selim-jerbi-b355a0202">
    <img src="https://img.shields.io/badge/LinkedIn-Connect%20with-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  &nbsp;
  <a href="mailto:selimjerbi66@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
</p>

<div align="center">
  <sub>CyberAtaraxia Careers — Open Source · Built with purpose by Selim JERBI</sub>
</div>
