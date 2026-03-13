# guide_for_PJPT_by-TCM-Secuirty

## Purpose
This repository is a practical study guide for TCM Security’s **PJPT** (Practical Junior Penetration Tester) and **PNPJT** (Practical Network Penetration Tester).

Focus:
- What to learn (skills + topics)
- What to practice (labs + drills)
- How to execute (methodology + time management)
- How to document (notes + reporting)

> Disclaimer: This guide is educational. Follow TCM’s exam rules and the law. Only test systems you own or have explicit permission to assess.

---

## Table of Contents
- [1) What these certifications test](#1-what-these-certifications-test)
- [2) Passing mindset](#2-passing-mindset)
- [3) Prep roadmap](#3-prep-roadmap)
- [4) Lab setup (safe practice)](#4-lab-setup-safe-practice)
- [5) PJPT checklist (core skills)](#5-pjpt-checklist-core-skills)
- [6) PNPJT checklist (network + AD leaning)](#6-pnpjts-checklist-network--ad-leaning)
- [7) PJPT vs PNPJT: key differences](#7-pjpt-vs-pnpjt-key-differences)
- [8) Tools to be fluent with](#8-tools-to-be-fluent-with)
- [9) Methodology (end-to-end workflow)](#9-methodology-end-to-end-workflow)
- [10) Privilege escalation quick guides](#10-privilege-escalation-quick-guides)
- [11) Active Directory / lateral movement essentials](#11-active-directory--lateral-movement-essentials)
  - [11.1) PNPJT quick workflow (beginner-friendly)](#111-pnpjt-quick-workflow-beginner-friendly)
  - [11.2) Active Directory Deep Dive (advanced)](#112-active-directory-deep-dive-advanced)
- [12) Reporting (what to include)](#12-reporting-what-to-include)
- [13) Time management during the exam](#13-time-management-during-the-exam)
- [14) Troubleshooting playbook (when stuck)](#14-troubleshooting-playbook-when-stuck)
- [15) Practice plans (2/4/6 weeks)](#15-practice-plans-246-weeks)
- [Appendix: command snippets](#appendix-command-snippets)

---

## 1) What these certifications test
### PJPT (Practical Junior Penetration Tester)
Typical expectations at a junior pentester level:
- Solid **recon + enumeration** (finding the real attack surface)
- Basic **web assessment** and service exploitation
- **Privilege escalation** fundamentals
- Clean, professional **reporting** with reproducible steps

### PNPJT (Practical Network Penetration Tester)
Usually more network- and enterprise-leaning:
- Strong **network service enumeration** and exploitation
- **Credential attacks** and pivoting/lateral-movement concepts
- **Active Directory fundamentals** (enumeration, common misconfigs)
- Documentation and operational discipline

> Always cross-check the **official exam objectives** (TCM may update scope).

---

## 2) Passing mindset
1. **Enumeration beats exploitation.** Most “hard” boxes are actually “missed info.”
2. **Write everything down immediately.** IPs, ports, creds, URLs, parameters, proof.
3. **Prove it.** Take screenshots and copy relevant command outputs.
4. **Stay systematic.** If stuck, return to recon with a checklist.
5. **Don’t tool-spam.** Automation helps, but understanding wins.

---

## 3) Prep roadmap
A reliable learning order:
1. Networking fundamentals (TCP/UDP, DNS, HTTP, SMB)
2. Linux essentials (users, permissions, services)
3. Windows basics (users/groups, services, file shares)
4. Scanning + enumeration discipline
5. Web fundamentals + common vulns
6. Privilege escalation (Linux first, Windows second)
7. Active Directory fundamentals (for PNPJT)
8. Reporting and note hygiene

---

## 4) Lab setup (safe practice)
Minimum:
- Kali Linux VM (or another pentest distro)
- Snapshot-capable hypervisor (VirtualBox/VMware)
- Notes app (Obsidian/CherryTree/Markdown)
- A practice platform (TryHackMe/HTB) and vulnerable VMs

### Suggested note template (per target)
- Target: IP/Hostname
- Scope/Rules:
- Recon:
  - nmap TCP:
  - nmap UDP:
  - web discovery:
- Services:
- Credentials:
- Exploitation:
- PrivEsc:
- Proof:
- Report narrative (clean steps):

---

## 5) PJPT checklist (core skills)
### Recon / scanning
- [ ] Run fast scans, then full TCP scans, then targeted UDP
- [ ] Interpret nmap results and enumerate each service properly

### Web enumeration
- [ ] Directory/file fuzzing (ffuf/gobuster)
- [ ] Virtual host checks (Host header)
- [ ] Basic Burp usage (Proxy, Repeater; Intruder if allowed)
- [ ] Common issues: default creds, weak auth, file upload, LFI/RFI basics, SQLi basics

### Service enumeration basics
- [ ] SMB shares and access checks
- [ ] FTP anonymous checks
- [ ] HTTP banner/app fingerprinting
- [ ] SSH version info + credential usage (only if creds found)

### Exploitation basics
- [ ] Searchsploit + manual validation
- [ ] Reverse shells + shell stabilization
- [ ] File transfers (wget/curl/scp)

### Linux privilege escalation
- [ ] `sudo -l` and GTFOBins use
- [ ] SUID enumeration
- [ ] Cron jobs and writable scripts
- [ ] Capabilities (`getcap`)
- [ ] Credential hunting in configs/backups/history

---

## 6) PNPJT checklist (network + AD leaning)
### Network enumeration
- [ ] Thorough service enumeration across multiple hosts
- [ ] Clear tracking of discovered hosts, ports, and credentials
- [ ] Password spraying / brute force only where allowed

### Credentials & movement
- [ ] Reuse discovered creds across services (SMB/WinRM/SSH/HTTP)
- [ ] Understand local vs domain creds
- [ ] Pivoting concepts (routing, port forwarding) if required

### Active Directory basics (high value)
- [ ] Identify domain, DC, and key services (DNS, LDAP, Kerberos, SMB)
- [ ] Enumerate users, groups, shares, policies where possible
- [ ] Recognize common AD attack paths (misconfig-driven)

---

## 7) PJPT vs PNPJT: key differences
### PJPT (typical emphasis)
- Single-host (or small set) compromise workflows
- Web enumeration + basic exploitation is common
- Linux privilege escalation is a frequent “make-or-break” area
- Focus on clear methodology and clean reporting

### PNPJT (typical emphasis)
- Wider network visibility: more targets and services
- Credential discovery and reuse matters more
- AD enumeration/attack-path thinking matters more
- Lateral movement/pivoting concepts may be required

How to adjust your prep:
- For PJPT: do many **easy-to-medium web/service boxes** and write mini reports.
- For PNPJT: do **network enumeration drills** and **credential tracking** exercises.

---

## 8) Tools to be fluent with
Core:
- `nmap`
- `ffuf` or `gobuster`
- `curl`, `wget`
- `nc` (netcat)
- Burp Suite
- `searchsploit`

Network/Windows (as appropriate):
- `smbclient`
- `enum4linux-ng`
- `crackmapexec` (NetExec)
- `impacket` tools (e.g., psexec/wmiexec/secretsdump) **only if allowed and in-scope**
- `evil-winrm` (if applicable)

PrivEsc helpers:
- `linpeas`, `winpeas` (if allowed)

---

## 9) Methodology (end-to-end workflow)
### Step 0: Read the rules twice
- Allowed attack types?
- Allowed tools?
- What counts as “proof”?
- Reporting format requirements?

### Step 1: Recon (start broad)
```bash
# Fast initial scan
nmap -Pn -n --top-ports 1000 -sV -sC <IP>

# Full TCP scan
nmap -Pn -n -p- -T4 -sV -sC <IP>

# Targeted UDP (don’t do full UDP unless required)
nmap -Pn -n -sU --top-ports 200 <IP>
```

### Step 2: Enumerate each service
For every open port, answer:
- What is it?
- What version/config?
- Anonymous/guest access?
- Can I read/write anything?
- Are there creds exposed?

### Step 3: Exploit carefully
- Verify versions and reproduce manually when possible.
- If an exploit fails: check prerequisites, endpoint paths, auth requirements, and mitigations.

### Step 4: Post-exploitation discipline
- Confirm user context: `whoami`, `id`, groups
- Collect key artifacts (configs, backups, tokens)
- Map escalation path

### Step 5: Privilege escalation
- Enumerate systematically, then test 1–2 best leads at a time.

---

## 10) Privilege escalation quick guides
### Linux quick commands
```bash
whoami
id
uname -a
sudo -l

# SUID
find / -perm -4000 -type f 2>/dev/null

# Capabilities
getcap -r / 2>/dev/null

# Cron
crontab -l 2>/dev/null
ls -la /etc/cron.*

# Common credential hunting
grep -R "password" -n /etc 2>/dev/null | head
ls -la /opt /var/backups /home 2>/dev/null
```

### Windows quick commands (baseline)
(Exact commands depend on what’s allowed and the environment.)
- Identify user and groups
- List services and check misconfigurations
- Search for stored credentials and readable sensitive files

---

## 11) Active Directory / lateral movement essentials
Common “must-know” concepts for network-focused practical exams:
- **Identify the domain**: hostnames, DNS, LDAP, Kerberos
- **Check SMB shares** on multiple hosts
- **Reuse creds** (password reuse is common)
- **Enumerate AD objects** if you have access (users/groups/computers)
- **Look for misconfigurations** rather than “magic exploits”

Operational advice:
- Keep a running **credential table** (username, password/hash, where found, where tested, result)
- Keep a running **host table** (IP, role, open ports, notes)

### 11.1) PNPJT quick workflow (beginner-friendly)
This is a “do this in order” workflow to keep you moving when the network feels large.

1) **Build your map**
- Run initial scans on every target you’re given.
- Track results in a host table: `IP → open ports → service → notes`.

2) **Prioritize high-signal services**
Look first at services that often lead to creds or access:
- SMB (shares, readable files)
- HTTP/HTTPS (apps, portals, admin panels)
- LDAP/Kerberos/DNS (domain signals)
- WinRM/SSH (direct remote access if creds exist)

3) **Enumerate SMB early and often**
- List shares.
- Check for readable files (configs, scripts, backups).
- Look for passwords in:
  - `*.txt`, `*.ini`, `*.config`, `*.xml`, `*.yml`, `*.ps1`

4) **Create a credential table (this is huge)**
Example columns:
- Username
- Password / Hash
- Source (where you found it)
- Validated on (host/service)
- Notes (local/domain/admin?)

5) **Credential reuse (controlled + documented)**
- When you find working creds, test them across:
  - SMB
  - WinRM
  - SSH
  - Web logins

6) **If AD exists, identify the DC and “center” services**
Clues:
- Hostnames mentioning `dc`, `ad`, `corp`, etc.
- Ports like LDAP/Kerberos/DNS.

7) **Only then go deeper**
If you have no foothold:
- return to web enumeration
- return to SMB file hunting
- expand scanning scope (if allowed)

### 11.2) Active Directory Deep Dive (advanced)
> Use this section once you’re comfortable with the beginner workflow. Keep everything within exam rules.

#### Key terminology (quick)
- **Domain Controller (DC):** central AD server (auth + directory)
- **LDAP:** directory queries (users/groups/computers)
- **Kerberos:** domain authentication protocol
- **SPN:** Service Principal Name (ties services to accounts)
- **ACL / DACL:** permissions on AD objects (who can do what)
- **GPO:** Group Policy (config + scripts pushed across machines)

#### High-level AD attack-path thinking
You’re usually trying to move from:
- *no creds* → *any creds* → *more privileges* → *high value access*

Common “paths” often involve:
- Weak/reused passwords
- Misconfigured shares containing secrets
- Over-permissive ACLs on users/groups
- Service accounts with interesting privileges
- GPOs or scripts that expose credentials

#### Kerberos (what to understand)
- Where Kerberos is used and why it matters.
- What “tickets” represent (auth artifacts).
- Why service accounts can be interesting.

#### LDAP enumeration (what to focus on)
If you can query LDAP, focus on:
- Domain users and groups
- Group memberships (who is admin-ish)
- Computers and their roles
- Any exposed descriptions/attributes that leak info

#### ACLs / permissions (conceptual checklist)
When you have some visibility into AD permissions, look for:
- Users/groups that can modify other users/groups
- Rights that allow resetting passwords or adding group members
- Delegated admin rights that can be abused

#### Practical discipline for advanced sections
- Keep notes of every query and result.
- Validate assumptions on the target.
- Avoid “random tool output dumps” in your report—extract the relevant evidence.

---

## 12) Reporting (what to include)
A strong report is:
- Reproducible
- Clear (headings, minimal noise)
- Evidence-driven (screenshots + outputs)

Suggested structure:
1. Executive summary (short)
2. Scope
3. Findings per host
   - Recon
   - Vulnerability
   - Exploitation steps
   - Impact
   - Remediation
4. Appendix (full scans)

---

## 13) Time management during the exam
A practical pacing strategy:
- 0–20% of time: scan everything; build the map
- 20–75%: exploit + escalate
- 75–100%: verify proof, clean steps, write/polish report

Rule of thumb: if stuck **30–45 minutes**, pivot:
- re-enumerate
- try a different service/host
- validate assumptions (wrong vhost? wrong creds? wrong URL?)

---

## 14) Troubleshooting playbook (when stuck)
- Reverse shell not coming back:
  - verify your callback IP/interface
  - verify listener port
  - test basic connectivity (ping/curl)
- Web dead end:
  - check vhosts/subdomains
  - fuzz directories and parameters
  - read source code and JS
- No privesc path:
  - expand enumeration (cron, SUID, capabilities, configs)
  - look for backups and reused passwords

---

## 15) Practice plans (2/4/6 weeks)
### 2-week crash plan
- Daily: 1–2 easy-to-medium boxes
- After each box: write a mini report (10–20 minutes)
- Focus: scanning + web enum + Linux privesc

### 4-week balanced plan
- Weeks 1–2: fundamentals + easy boxes
- Week 3: intermediate boxes + Windows basics
- Week 4: timed mock exam + full report

### 6-week strong plan
- Add AD-focused practice (PNPJT)
- Add more web variety (uploads, auth issues, LFI/SSTI basics)
- Create your own repeatable checklists

---

## Appendix: command snippets
### Web fuzzing
```bash
ffuf -u http://<IP>/FUZZ -w /usr/share/wordlists/dirb/common.txt

# Vhost fuzz (adjust domain)
ffuf -u http://<IP>/ -H "Host: FUZZ.example.local" -w <wordlist>
```

### SMB enumeration
```bash
smbclient -L //<IP>/ -N
smbclient //<IP>/<share> -N
```

### Shell stabilization (Linux)
```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm
stty raw -echo; fg
```