# OSINT & Security Research Tools

## Key Topics
- Advanced Google search operators
- Passive reconnaissance tools (Shodan, Censys, Maltego, theHarvester)
- Malware analysis (VirusTotal)
- Active reconnaissance (Nmap, OWASP Amass)
- Network analysis (Wireshark)
- CVE database

---

## Introduction

OSINT (Open Source Intelligence) is the process of collecting information about a target using **publicly available sources** — no hacking required. It's the first phase of almost every penetration test or security investigation.

```
Reconnaissance → Scanning → Exploitation → Post-Exploitation
      ↑
  OSINT lives here
```

---

## Google Search Operators

Before using specialised tools, you can extract a lot of information from Google using advanced search operators.

| Operator          | Purpose                                                  | Example                          |
|-------------------|----------------------------------------------------------|----------------------------------|
| `"exact phrase"`  | Search for an exact word or sentence                     | `"default admin password"`       |
| `site:`           | Limit results to a specific domain                       | `site:tryhackme.com`             |
| `-word`           | Exclude a word from results                              | `pyramids -tourism`              |
| `filetype:`       | Search for a specific file type                          | `filetype:ppt cybersecurity`     |
| `intitle:`        | Search for pages with a keyword in the title             | `intitle:"index of"`             |
| `inurl:`          | Search for pages with a keyword in the URL               | `inurl:admin`                    |

### Google Dorking in Security
Combining operators to find sensitive exposed data is called **Google Dorking**:

```
filetype:pdf "confidential" site:gov
intitle:"index of" "passwords"
site:company.com filetype:xlsx
```

> Google Dorking is passive — you're only using what's already publicly indexed.

---

## Shodan

Shodan is a search engine for **internet-connected devices**. Instead of indexing web pages, it scans the internet for open ports and services.

### What It Does
- Scans the internet for open ports and running services
- Collects **banners** — information that services reveal about themselves
- Lets you search for exposed or misconfigured devices

### What You Can Find
- Open webcams and IP cameras
- Misconfigured servers
- Publicly exposed databases
- Industrial control systems (ICS/SCADA)
- Devices running outdated/vulnerable software

### Example Search
```
apache country:MA port:22 ubuntu
```
This finds Apache servers in Morocco, with port 22 open, running Ubuntu.

### Useful Shodan Filters

| Filter        | Purpose                              |
|---------------|--------------------------------------|
| `country:`    | Filter by country code               |
| `port:`       | Filter by port number                |
| `os:`         | Filter by operating system           |
| `org:`        | Filter by organisation / ISP         |
| `hostname:`   | Filter by hostname                   |

---

## VirusTotal

VirusTotal is a free online malware analysis platform. You upload something and it checks it against **70+ antivirus engines** simultaneously.

### What It Scans
- Files (executables, documents, archives)
- URLs
- IP addresses
- Domains

### What It Shows
- Whether the file or URL is flagged as malicious
- Which specific AV engines detected it and what they call it
- Behaviour reports (sandbox analysis)
- Related malware samples and campaigns

### How Security People Use It
- Analyse suspicious files received via email
- Investigate phishing links before clicking
- Track malware campaigns and identify related samples
- Quickly triage IOCs (Indicators of Compromise)

> If even 1–2 engines flag something, treat it as suspicious. If 30+ flag it, it's almost certainly malicious.

---

## Censys

Censys is similar to Shodan but more **research-focused and structured**. It continuously scans the internet and organises its findings in a queryable database.

### What It Collects
- Open ports and services
- TLS/SSL certificates
- Services running on hosts
- Internet infrastructure data

### What It's Good At

| Use Case                         | Why Censys                                      |
|----------------------------------|-------------------------------------------------|
| Finding domains on same cert     | Certificate transparency logs                   |
| Mapping company infrastructure   | Structured host and domain data                 |
| Discovering subdomains           | Passive, no direct interaction with target      |
| Analysing SSL/TLS certificates   | Rich certificate metadata                       |

### Example Uses
- Find all servers belonging to a specific organisation
- Discover subdomains via certificate data
- Identify exposed services across an IP range

---

## Maltego

Maltego is a **visual investigation and link analysis tool**. Instead of showing lists of results, it builds **relationship graphs** between entities.

### What You Can Map
- Domains and subdomains
- Email addresses
- IP addresses
- Phone numbers
- Companies and people
- Social media profiles

### Why It's Useful
- Visually connects the dots between pieces of intelligence
- Reveals hidden relationships between entities
- Widely used in threat intelligence and corporate investigations
- Supports automated data gathering via **transforms** (built-in queries)

---

## theHarvester

theHarvester is a command-line OSINT tool that collects **emails, subdomains, IPs, and hostnames** from public sources.

### Data Sources It Queries
- Google, Bing, DuckDuckGo
- LinkedIn
- DNS records
- Security databases (Shodan, Censys, etc.)

### Example Command
```bash
theHarvester -d company.com -b google
```

| Flag  | Purpose                              |
|-------|--------------------------------------|
| `-d`  | Target domain                        |
| `-b`  | Data source to query                 |
| `-l`  | Limit number of results              |
| `-f`  | Save output to a file                |

### What It Returns
- Email addresses found publicly
- Subdomains
- Hosts and IP addresses

> Pentesters use this heavily in the **early reconnaissance phase** to build a target profile before doing anything active.

---

## Nmap

Nmap (Network Mapper) is one of the most important tools in cybersecurity. It's used to discover **open ports, running services, and OS information** on a target machine.

### What It Tells You
- Which ports are open
- What services are running on those ports
- What OS the machine might be using
- Service version numbers (important for finding vulnerabilities)

### Basic Commands

```bash
nmap 10.10.10.10              # basic scan
nmap -sV 10.10.10.10          # detect service versions
nmap -sC 10.10.10.10          # run default scripts
nmap -A 10.10.10.10           # aggressive scan (OS, versions, scripts)
nmap -p 80,443,22 10.10.10.10 # scan specific ports
nmap -p- 10.10.10.10          # scan all 65535 ports
```

### Example Output
```
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 7.6
80/tcp  open  http    Apache 2.4.29
443/tcp open  https   nginx 1.14
```

This tells you exactly what the **attack surface** looks like — what's running and potentially exploitable.

### Common Nmap Flags

| Flag   | Purpose                                     |
|--------|---------------------------------------------|
| `-sV`  | Detect service versions                     |
| `-sC`  | Run default NSE scripts                     |
| `-A`   | Aggressive — OS detection, versions, scripts|
| `-p-`  | Scan all 65535 ports                        |
| `-T4`  | Faster scan speed                           |
| `-oN`  | Save output to a file                       |
| `-Pn`  | Skip host discovery (treat host as up)      |

---

## OWASP Amass

Amass is used for **subdomain enumeration and attack surface mapping**. It discovers subdomains passively and actively through DNS, certificates, and APIs.

### Example Discovery
```
Target: example.com

Amass finds:
  mail.example.com
  vpn.example.com
  dev.example.com
  api.example.com
  staging.example.com
```

### Why This Matters
- Companies often forget old development or staging servers
- These forgotten subdomains are frequently unpatched and misconfigured
- A dev server exposed to the internet is a common entry point
- **Bug bounty hunters** rely heavily on this tool

```bash
amass enum -d example.com           # passive enumeration
amass enum -active -d example.com   # active enumeration
```

---

## Wireshark

Wireshark is a **network packet analyser** — it lets you capture and inspect actual network traffic in real time.

### What You Can Inspect
- HTTP requests and responses
- DNS queries and responses
- TCP handshakes
- Credentials sent over unencrypted connections
- Malware communicating with C2 servers

### Use Cases

| Context        | How Wireshark Helps                                           |
|----------------|---------------------------------------------------------------|
| Networking     | Debugging slow or broken connections                          |
| Blue Team      | Detecting unusual traffic patterns or exfiltration            |
| Malware Analysis | Watching what a malicious file communicates with            |
| CTF / Learning | Understanding how protocols actually work at packet level     |

### Key Features
- Live capture on any network interface
- Filter traffic with display filters: `http`, `dns`, `tcp.port == 80`
- Follow TCP streams to reconstruct full conversations
- Export captured packets for offline analysis

```
Filter examples:
http.request.method == "POST"     # show only POST requests
dns                                # show only DNS traffic
ip.addr == 10.10.10.10            # filter by IP address
```

---

## CVE — Common Vulnerabilities and Exposures

The **CVE database** is a public catalogue of known security vulnerabilities. Every discovered vulnerability gets a unique CVE ID.

### CVE ID Format
```
CVE-YEAR-NUMBER
CVE-2021-44228   ← Log4Shell (critical Apache Log4j vulnerability)
CVE-2017-0144    ← EternalBlue (used in WannaCry ransomware)
```

### What a CVE Entry Contains
- Description of the vulnerability
- Affected software and versions
- CVSS score (severity rating 0–10)
- References to patches and advisories

### CVSS Severity Scale

| Score   | Severity |
|---------|----------|
| 0.0     | None     |
| 0.1–3.9 | Low      |
| 4.0–6.9 | Medium   |
| 7.0–8.9 | High     |
| 9.0–10  | Critical |

### Where to Look Up CVEs
- https://cve.mitre.org
- https://nvd.nist.gov (National Vulnerability Database)
- https://www.exploit-db.com (exploits linked to CVEs)

---

## Tool Summary

| Tool           | Type       | Main Use                                              |
|----------------|------------|-------------------------------------------------------|
| Google Dorks   | Passive    | Find exposed data indexed by search engines           |
| Shodan         | Passive    | Search for exposed devices and open ports             |
| VirusTotal     | Passive    | Scan files, URLs, and IPs against 70+ AV engines      |
| Censys         | Passive    | Map internet infrastructure and certificates          |
| Maltego        | Passive    | Visual relationship mapping between entities          |
| theHarvester   | Passive    | Collect emails, subdomains, IPs from public sources   |
| Nmap           | Active     | Port scanning, service detection, OS fingerprinting   |
| OWASP Amass    | Both       | Subdomain enumeration and attack surface mapping      |
| Wireshark      | Active     | Capture and analyse live network traffic              |
| CVE Database   | Reference  | Look up known vulnerabilities and their severity      |

---

## Takeaways
- OSINT is the first step of any recon — collect as much as possible without touching the target
- Shodan and Censys can reveal what a company has exposed to the internet without them knowing
- VirusTotal is the fastest way to triage a suspicious file or link
- Nmap is non-negotiable — knowing what's open on a machine defines your attack surface
- Forgotten subdomains and dev servers are common entry points — Amass finds them
- Wireshark is essential for understanding what's actually happening on a network
- CVEs give vulnerabilities a name and a severity — always check if your target version is patched
