# Guide: How to Successfully Pass PJPT & PNPT by TCM Security

> A practical, community-sourced study guide for the **Practical Junior Penetration Tester (PJPT)** and **Practical Network Penetration Tester (PNPT)** certifications offered by [TCM Security](https://tcm-sec.com/).

---

## Table of Contents

1. [About TCM Security Certifications](#about-tcm-security-certifications)
2. [PJPT – Practical Junior Penetration Tester](#pjpt--practical-junior-penetration-tester)
   - [Overview](#pjpt-overview)
   - [Exam Format](#pjpt-exam-format)
   - [Topics Covered](#pjpt-topics-covered)
   - [Recommended Courses](#pjpt-recommended-courses)
   - [Study Plan](#pjpt-study-plan)
   - [Lab Setup](#pjpt-lab-setup)
   - [Tips for Passing](#pjpt-tips-for-passing)
3. [PNPT – Practical Network Penetration Tester](#pnpt--practical-network-penetration-tester)
   - [Overview](#pnpt-overview)
   - [Exam Format](#pnpt-exam-format)
   - [Topics Covered](#pnpt-topics-covered)
   - [Recommended Courses](#pnpt-recommended-courses)
   - [Study Plan](#pnpt-study-plan)
   - [Lab Setup](#pnpt-lab-setup)
   - [Tips for Passing](#pnpt-tips-for-passing)
4. [Essential Tools Reference](#essential-tools-reference)
5. [General Study Tips](#general-study-tips)
6. [Additional Resources](#additional-resources)

---

## About TCM Security Certifications

TCM Security provides **affordable, hands-on, practical** cybersecurity certifications. Unlike multiple-choice exams, both PJPT and PNPT require you to **actually compromise machines**, demonstrate your methodology, and write a professional penetration testing report.

| Certification | Level | Focus | Duration |
|---|---|---|---|
| PJPT | Entry-level | Internal network, AD basics | 48-hour exam |
| PNPT | Intermediate | Full external + internal network | 5-day exam |

---

## PJPT – Practical Junior Penetration Tester

### PJPT Overview

The **PJPT** is an entry-level certification designed for those new to penetration testing. It validates your ability to perform a basic internal network penetration test and write a professional report.

**Cost:** ~$200 USD (includes one free retake)  
**Prerequisites:** None (formal prerequisites), but basic networking and Linux knowledge is highly recommended  
**Validity:** Does not expire

### PJPT Exam Format

- **Duration:** 48 hours to complete the penetration test + 24 hours to submit the report (total 5 days)
- **Format:** Practical exam on a virtual network — you must compromise a specific target
- **Deliverable:** Written penetration testing report
- **Passing score:** Pass/Fail based on TCM Security's review of your report

### PJPT Topics Covered

The exam tests skills across these core areas:

#### Networking Fundamentals
- TCP/IP model and protocols (TCP, UDP, ICMP, DNS, DHCP)
- Common ports and services (21 FTP, 22 SSH, 23 Telnet, 25 SMTP, 53 DNS, 80/443 HTTP/S, 139/445 SMB, 3389 RDP)
- Subnetting basics
- Understanding of network traffic and packet analysis

#### Linux & Command Line
- Basic Linux navigation (`ls`, `cd`, `cat`, `grep`, `find`, `chmod`)
- File permissions and user management
- Networking commands (`ifconfig`/`ip a`, `netstat`, `ping`, `traceroute`)
- Bash scripting basics

#### Reconnaissance
- Passive reconnaissance (OSINT basics)
- Active reconnaissance with `nmap`
- Service and version enumeration

#### Scanning & Enumeration
- Port scanning with `nmap` (SYN scan, service detection, OS detection, script scanning)
- SMB enumeration (`enum4linux`, `smbclient`, `crackmapexec`)
- Web application enumeration (basic directory busting with `gobuster`/`ffuf`)

#### Exploitation
- Using Metasploit Framework
- Exploiting common vulnerabilities (EternalBlue MS17-010, etc.)
- Manual exploitation basics
- Password attacks and credential stuffing
- Pass-the-Hash (PtH) attacks

#### Active Directory (AD) Basics
- AD structure: domains, forests, OUs, users, groups
- LLMNR/NBT-NS poisoning with `Responder`
- SMB relay attacks
- Kerberoasting
- AS-REP Roasting
- Token impersonation
- Basic AD enumeration with `BloodHound`/`SharpHound`

#### Post-Exploitation
- Privilege escalation (Windows and Linux basics)
- Credential dumping with `Mimikatz`
- Pivoting basics
- Maintaining access

#### Report Writing
- Executive summary
- Technical findings with severity ratings (Critical, High, Medium, Low, Informational)
- Proof-of-concept (PoC) screenshots
- Remediation recommendations

### PJPT Recommended Courses

These TCM Security courses directly prepare you for the PJPT:

| Course | Platform | Priority |
|---|---|---|
| [Practical Ethical Hacking (PEH)](https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course) | TCM Academy | ⭐ Essential |
| [Linux Privilege Escalation for Beginners](https://academy.tcm-sec.com/p/linux-privilege-escalation) | TCM Academy | Recommended |
| [Windows Privilege Escalation for Beginners](https://academy.tcm-sec.com/p/windows-privilege-escalation-for-beginners) | TCM Academy | Recommended |

### PJPT Study Plan

**Estimated time:** 4–8 weeks (depending on experience)

#### Week 1–2: Foundations
- [ ] Complete the Networking section of Practical Ethical Hacking (PEH)
- [ ] Set up your Kali Linux VM and practice basic Linux commands
- [ ] Learn `nmap` thoroughly — scanning options, output formats, NSE scripts
- [ ] Practice SMB enumeration

#### Week 3–4: Core Attack Techniques
- [ ] Complete the Active Directory section of PEH
- [ ] Practice LLMNR/NBT-NS poisoning with Responder in a home lab
- [ ] Learn and practice SMB relay attacks
- [ ] Study Kerberoasting and AS-REP Roasting

#### Week 5–6: Exploitation & Post-Exploitation
- [ ] Work through Metasploit modules in PEH
- [ ] Practice Mimikatz and credential dumping
- [ ] Set up a small Active Directory home lab (2 Windows VMs + 1 Kali)
- [ ] Practice the full attack chain end-to-end

#### Week 7–8: Report Writing & Review
- [ ] Write mock penetration test reports
- [ ] Review all attack techniques from memory
- [ ] Do a full mock exam on your home lab
- [ ] Review the TCM Security report template

### PJPT Lab Setup

Build a minimal home lab to practice:

```
[Kali Linux Attacker]  ←→  [Windows Server 2019/2022 (Domain Controller)]
                       ←→  [Windows 10/11 (Domain-joined workstation)]
```

**Requirements:**
- **Hypervisor:** VirtualBox (free) or VMware Workstation Pro/Player
- **Kali Linux:** [kali.org/get-kali](https://www.kali.org/get-kali/) (recommended: 2+ GB RAM, 2 CPU cores)
- **Windows Server:** Use a free evaluation ISO from Microsoft (~180-day trial)
- **Windows 10/11:** Use a free evaluation ISO from Microsoft
- **RAM:** Minimum 8 GB host RAM recommended (16 GB ideal)
- **Network:** Set all VMs to **Host-Only** or **Internal Network** adapter

**Quick AD lab setup steps:**
1. Install Windows Server and promote it to a Domain Controller (e.g., `lab.local`)
2. Create 2–3 user accounts with weak/reused passwords
3. Join Windows 10 machine to the domain
4. Configure some misconfigured services (e.g., enable SMB signing disabled, add SPNs for Kerberoasting)
5. Use Kali Linux as your attacking machine on the same network segment

### PJPT Tips for Passing

1. **Follow the methodology** — Don't skip enumeration. Document everything.
2. **Take detailed notes** — Screenshot every step. You'll need these for the report.
3. **Know your AD attack chain** — LLMNR poisoning → SMB relay → credential access → lateral movement is a common path.
4. **Practice Responder + ntlmrelayx** — Understand how the relay chain works, not just how to run it.
5. **BloodHound is your friend** — Run SharpHound, ingest data, and find attack paths visually.
6. **Report quality matters** — A technically successful exam with a poor report can mean failure. Write clearly, include screenshots, and provide remediation steps.
7. **Manage your time** — 48 hours is ample time. Don't panic. Sleep and come back fresh if stuck.
8. **Read the exam instructions carefully** — Know exactly what you need to compromise.
9. **Don't overthink it** — The PJPT is entry-level. Focus on the basics done well.
10. **Use the TCM report template** — TCM Security provides a report template. Use it.

---

## PNPT – Practical Network Penetration Tester

### PNPT Overview

The **PNPT** is an intermediate-level certification that simulates a real-world network penetration test engagement. It covers external reconnaissance through internal network compromise, including Active Directory attacks and a professional report deliverable.

**Cost:** ~$400 USD (includes one free retake)  
**Prerequisites:** None (formal prerequisites), but PJPT-level skills or equivalent experience recommended  
**Validity:** Does not expire

### PNPT Exam Format

- **Duration:** 5 days (120 hours) to complete the penetration test + 2 additional days to submit the report
- **Format:** Practical exam simulating a full external-to-internal engagement
  - Day 1–2: External reconnaissance and initial access
  - Day 2–5: Internal network compromise and Active Directory attacks
- **Deliverable:** Professional penetration testing report
- **Debrief:** A 15-minute live video debrief with a TCM Security assessor after submission
- **Passing:** Pass/Fail based on report quality and debrief performance

### PNPT Topics Covered

The PNPT builds on PJPT topics and adds depth in the following areas:

#### Advanced Reconnaissance & OSINT
- Passive recon: `theHarvester`, `Maltego`, `Shodan`, `Hunter.io`, `LinkedIn`
- Subdomain enumeration: `subfinder`, `amass`, `assetfinder`
- Certificate transparency logs
- Breached credential research
- Google Dorking techniques
- Email harvesting

#### External Network Assessment
- Full port scanning and service fingerprinting
- Web application testing basics (OWASP Top 10 awareness)
- VPN and firewall enumeration
- Identifying public-facing attack surface

#### Active Directory – Deep Dive
- Full AD attack chain from external to Domain Admin
- `BloodHound`/`SharpHound` data collection and path analysis
- Pass-the-Hash (PtH) and Pass-the-Ticket (PtT)
- DCSync attack (dump all domain credentials)
- Golden Ticket and Silver Ticket attacks
- AD CS (Certificate Services) attacks: ESC1–ESC8
- ADIDNS abuse
- LDAP enumeration and attacks
- Group Policy abuse
- ACL/ACE abuse (GenericAll, WriteDACL, ForceChangePassword, etc.)
- Constrained and unconstrained delegation attacks

#### Web Application Exploitation (Basic)
- Directory and file enumeration (`gobuster`, `ffuf`, `feroxbuster`)
- Common web vulnerabilities: SQLi, XSS, File inclusion, command injection
- CMS exploitation (WordPress, Joomla) with `wpscan`
- Default credentials

#### Exploitation & Post-Exploitation
- Manual exploitation without Metasploit (scripted PoC and manual techniques)
- Pivoting and tunneling with `chisel`, `sshuttle`, `proxychains`
- Port forwarding
- Credential harvesting and reuse
- Living-off-the-land (LOLBins) techniques

#### Wireless Attacks (Awareness)
- WPA2 handshake capture and offline cracking
- Evil twin attacks
- Wireless reconnaissance

#### Report Writing – Professional Level
- Executive summary for non-technical stakeholders
- Detailed technical narrative of the attack path
- Risk-rated findings with CVSS scores
- Clear remediation guidance
- Appendices: scan output, tool usage, timeline

### PNPT Recommended Courses

Complete these TCM Security courses to fully prepare:

| Course | Platform | Priority |
|---|---|---|
| [Practical Ethical Hacking (PEH)](https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course) | TCM Academy | ⭐ Essential |
| [Practical OSINT](https://academy.tcm-sec.com/p/osint-fundamentals) | TCM Academy | ⭐ Essential |
| [Practical Web Application Security & Testing](https://academy.tcm-sec.com/p/practical-web-application-security-and-testing) | TCM Academy | ⭐ Essential |
| [Linux Privilege Escalation for Beginners](https://academy.tcm-sec.com/p/linux-privilege-escalation) | TCM Academy | Recommended |
| [Windows Privilege Escalation for Beginners](https://academy.tcm-sec.com/p/windows-privilege-escalation-for-beginners) | TCM Academy | Recommended |
| [Practical Malware Analysis & Triage](https://academy.tcm-sec.com/p/practical-malware-analysis-triage) | TCM Academy | Optional |
| [External Pentest Playbook](https://academy.tcm-sec.com/p/external-pentest-playbook) | TCM Academy | Recommended |

**Supplementary platforms:**
- [TryHackMe](https://tryhackme.com) — Active Directory and network rooms
- [HackTheBox](https://hackthebox.com) — Intermediate/advanced machines
- [PentesterLab](https://pentesterlab.com) — Web application practice

### PNPT Study Plan

**Estimated time:** 8–16 weeks (depending on experience)

#### Week 1–2: OSINT & External Recon Mastery
- [ ] Complete the TCM Practical OSINT course
- [ ] Practice subdomain enumeration with `amass` and `subfinder`
- [ ] Learn Google Dorking — practice on test targets
- [ ] Practice `theHarvester` for email and subdomain gathering
- [ ] Understand how to identify an organization's attack surface

#### Week 3–4: Web Application Basics
- [ ] Complete TCM Practical Web Application Security & Testing
- [ ] Practice on DVWA (Damn Vulnerable Web Application)
- [ ] Learn directory busting with `gobuster` and `ffuf`
- [ ] Study common OWASP Top 10 vulnerabilities with hands-on practice
- [ ] Practice exploiting WordPress with `wpscan`

#### Week 5–7: Advanced Active Directory Attacks
- [ ] Review and deepen the AD section of PEH
- [ ] Set up a full AD lab (DC + 2–3 workstations + Kali)
- [ ] Practice full attack chain: Responder → relay → Kerberoasting → BloodHound → DCSync
- [ ] Study and practice ACL abuse techniques
- [ ] Learn and practice AD CS attacks (use the `Certipy` tool)
- [ ] Practice Pass-the-Ticket and Golden/Silver Ticket attacks

#### Week 8–10: Exploitation & Post-Exploitation
- [ ] Practice pivoting with `chisel` and `proxychains`
- [ ] Practice privilege escalation (both Windows and Linux)
- [ ] Learn and practice DCSync with `Mimikatz` and `secretsdump.py`
- [ ] Practice lateral movement techniques
- [ ] Study LOLBins and living-off-the-land techniques

#### Week 11–12: External Pentest Methodology
- [ ] Complete the TCM External Pentest Playbook course
- [ ] Practice a full simulated external assessment
- [ ] Chain together: OSINT → web recon → initial access → internal pivot → AD compromise

#### Week 13–14: Report Writing
- [ ] Study sample PNPT reports shared by the community
- [ ] Write 2–3 full mock reports from previous lab work
- [ ] Practice the executive summary section (non-technical writing)
- [ ] Review CVSS scoring methodology
- [ ] Practice giving a verbal debrief (the PNPT includes a live debrief)

#### Week 15–16: Review & Mock Exam
- [ ] Full mock assessment on your home lab (5-day simulation)
- [ ] Gap analysis — revisit weak areas
- [ ] Practice the debrief presentation
- [ ] Rest and schedule your exam

### PNPT Lab Setup

A more comprehensive lab than PJPT:

```
[Kali Linux]  ←→  [Firewall/Router VM (pfSense optional)]
                  ├── [Windows Server 2019/2022 – Domain Controller]
                  ├── [Windows Server 2019 – Member Server (AD CS optional)]
                  ├── [Windows 10/11 – Workstation 1]
                  ├── [Windows 10/11 – Workstation 2]
                  └── [Ubuntu/CentOS – Linux server (optional)]
```

**Recommended resources:**
- TCM Security's free [AD Lab Setup guide](https://github.com/The-Hacker-Recipes) in PEH
- [VulnAD](https://github.com/WazeHell/vulnerable-AD) — Automated vulnerable AD lab setup script
- [GOAD (Game of Active Directory)](https://github.com/Orange-Cyberdefense/GOAD) — Advanced multi-forest AD lab

### PNPT Tips for Passing

1. **Master OSINT before everything else** — The exam starts externally. Strong reconnaissance reveals the most viable attack paths.
2. **Document obsessively** — Keep a running notes file (CherryTree, Obsidian, or Notion). Log every command, output, and finding.
3. **Understand the full attack chain** — Don't just memorize commands. Understand *why* each attack works.
4. **BloodHound first, always** — After gaining initial internal access, run SharpHound and analyze paths to Domain Admin immediately.
5. **Know your pivoting tools** — `chisel` + `proxychains` is a common combination. Practice until it's second nature.
6. **Prepare for the debrief** — Practice explaining your attack path clearly. The debrief is 15 minutes — be concise and confident.
7. **Report structure matters** — TCM assessors read many reports. A clean, structured, professional report stands out.
8. **Don't skip the executive summary** — Executives and managers read this. Write it for a non-technical audience.
9. **Pace yourself** — You have 5 days. Work in focused sessions, take breaks, sleep. Fatigue leads to mistakes.
10. **Retake is included** — Don't let exam anxiety overwhelm you. One free retake is included with purchase.
11. **Join the TCM Security Discord** — A very active community. Search before asking; most questions have been answered.
12. **Manual exploitation counts more** — Demonstrating manual exploitation techniques (not just auto-exploits) shows depth.

---

## Essential Tools Reference

### Reconnaissance
| Tool | Purpose | Command Example |
|---|---|---|
| `nmap` | Port scanning | `nmap -sC -sV -oA scan <target>` |
| `theHarvester` | Email/subdomain harvest | `theHarvester -d target.com -b all` |
| `subfinder` | Subdomain enumeration | `subfinder -d target.com` |
| `amass` | Attack surface mapping | `amass enum -d target.com` |
| `shodan` | Internet-exposed assets | Search via web or CLI |

### Active Directory
| Tool | Purpose | Command Example |
|---|---|---|
| `Responder` | LLMNR/NBT-NS poisoning | `sudo responder -I eth0 -dPv` |
| `ntlmrelayx.py` | SMB relay | `ntlmrelayx.py -tf targets.txt -smb2support` |
| `BloodHound` | AD attack path visualization | Run SharpHound, ingest data |
| `CrackMapExec` | AD Swiss Army knife | `cme smb <target> -u user -p pass` |
| `Mimikatz` | Credential dumping | `sekurlsa::logonpasswords` |
| `Rubeus` | Kerberos attacks | `Rubeus.exe kerberoast` |
| `Impacket` | AD/network attacks | `secretsdump.py`, `psexec.py`, `GetUserSPNs.py` |
| `Certipy` | AD CS attacks | `certipy find -u user@domain -p pass` |

### Exploitation
| Tool | Purpose | Command Example |
|---|---|---|
| `Metasploit` | Exploitation framework | `msfconsole` |
| `searchsploit` | Offline exploit database | `searchsploit <service> <version>` |
| `hydra` | Online password attacks | `hydra -l user -P wordlist.txt ssh://<target>` |
| `hashcat` | Offline password cracking | `hashcat -m 1000 hashes.txt rockyou.txt` |
| `john` | Offline password cracking | `john --wordlist=rockyou.txt hashes.txt` |

### Web Application
| Tool | Purpose | Command Example |
|---|---|---|
| `gobuster` | Directory/file busting | `gobuster dir -u http://target -w wordlist.txt` |
| `ffuf` | Fuzzing | `ffuf -u http://target/FUZZ -w wordlist.txt` |
| `wpscan` | WordPress scanner | `wpscan --url http://target --enumerate` |
| `nikto` | Web vulnerability scanner | `nikto -h http://target` |
| `Burp Suite` | Web proxy / manual testing | GUI-based |

### Post-Exploitation & Pivoting
| Tool | Purpose | Command Example |
|---|---|---|
| `chisel` | TCP/SOCKS tunneling | `chisel server/client` combo |
| `proxychains` | Route traffic via proxy | `proxychains nmap -sT <internal-target>` |
| `sshuttle` | VPN-over-SSH | `sshuttle -r user@pivot 10.10.10.0/24` |
| `linpeas` | Linux privilege escalation | `./linpeas.sh` |
| `winpeas` | Windows privilege escalation | `.\winpeas.exe` |

---

## General Study Tips

1. **Learn the "why" not just the "how"** — Understand the underlying vulnerability, not just the tool syntax. This helps when tools fail or environments differ.

2. **Build a home lab** — Hands-on practice is irreplaceable. Spin up VMs and break things safely.

3. **Take structured notes** — Use tools like [Obsidian](https://obsidian.md/), [CherryTree](https://www.giuspen.net/cherrytree/), or [Notion](https://www.notion.so/) to organize techniques, commands, and findings.

4. **Practice report writing early** — Don't save it for last. Write reports on your lab practice sessions.

5. **Use community resources** — The TCM Security Discord, YouTube, and write-ups from others who have passed are invaluable.

6. **Simulate time pressure** — During exam prep, practice completing tasks within time limits to build speed.

7. **Study common wordlists** — Know `rockyou.txt`, `SecLists`, and `seclists/Discovery/Web-Content/` paths by heart.

8. **Learn PowerShell** — Many Windows-based post-exploitation techniques require at least basic PowerShell knowledge.

9. **Review TCM Security's free content** — Heath Adams (The Cyber Mentor) posts free content on [YouTube](https://www.youtube.com/c/TheCyberMentor) that aligns with the exam content.

10. **Be patient** — Penetration testing is a skill built over time. Consistency beats intensity.

---

## Additional Resources

### Official
- [TCM Security Academy](https://academy.tcm-sec.com/) — Official courses
- [TCM Security Discord](https://discord.gg/tcm) — Community support and hints
- [TCM Security Blog](https://tcm-sec.com/blog/) — Free articles and walkthroughs

### Free Practice Platforms
- [TryHackMe](https://tryhackme.com) — Beginner-friendly rooms
- [HackTheBox](https://hackthebox.com) — Intermediate+ machines
- [VulnHub](https://vulnhub.com) — Downloadable vulnerable VMs
- [PortSwigger Web Security Academy](https://portswigger.net/web-security) — Free web app labs

### Key YouTube Channels
- [The Cyber Mentor (TCM)](https://www.youtube.com/c/TheCyberMentor) — Course author's channel
- [IppSec](https://www.youtube.com/c/ippsec) — HTB machine walkthroughs
- [John Hammond](https://www.youtube.com/c/JohnHammond010) — CTF and security content
- [NetworkChuck](https://www.youtube.com/c/NetworkChuck) — Networking and Linux basics

### Wordlists & Cheat Sheets
- [SecLists](https://github.com/danielmiessler/SecLists) — Essential wordlist collection
- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings) — Attack payloads reference
- [HackTricks](https://book.hacktricks.xyz/) — Comprehensive pentesting wiki
- [PNPT/PJPT Cheat Sheet by TCM](https://github.com/TCM-Course-Resources) — Official course resources

### Community Write-ups
Search for "PJPT pass" or "PNPT pass" on:
- [Medium](https://medium.com) — Many community write-ups shared after passing
- [Reddit r/netsecstudents](https://reddit.com/r/netsecstudents)
- [TCM Security Discord #certification-chat](https://discord.gg/tcm)

---

*This guide is community-maintained. Contributions and corrections are welcome via pull request.*