# Cryptography Basics

## Key Topics
- Core cryptography terminology
- The CIA Triad
- Symmetric encryption & the Caesar Cipher
- Asymmetric encryption & how it works

---

## Core Terminology

| Term        | Definition                                                                                   |
|-------------|----------------------------------------------------------------------------------------------|
| Plaintext   | A readable message — e.g. `HELLO` or `Patient name: Alice Smith`                            |
| Ciphertext  | The scrambled, unreadable version — e.g. `KHOOR` or `Sdwlhqw qdph: Dolfh Vplwk`            |
| Key         | The secret ingredient that controls how scrambling and unscrambling works                    |
| Algorithm   | The public recipe — the steps that explain how to apply the key to a message                 |

> Security doesn't come from hiding the algorithm — it comes from keeping the **key** secret.

### Encryption & Decryption Flow

```
Plaintext  + Algorithm + Key  →  Ciphertext   (Encryption)
Ciphertext + Algorithm + Key  →  Plaintext    (Decryption)
```

---

## The CIA Triad

The CIA Triad is the foundation of information security. Every security decision should protect at least one of these three principles:

```
        Confidentiality
             🔒
            /    \
           /      \
    Integrity ── Availability
        ✅            ⚡
```

### Confidentiality
- Ensures that information is only accessible to those authorised to see it
- Enforced through: encryption, access controls, authentication
- Example: Encrypting a patient's medical records so only doctors can read them

### Integrity
- Ensures that data has not been tampered with or altered
- Enforced through: hashing, digital signatures, checksums
- Example: Verifying a downloaded file hasn't been corrupted or modified

### Availability
- Ensures that systems and data are accessible when needed
- Enforced through: backups, redundancy, DDoS protection, uptime monitoring
- Example: A hospital's systems staying online even during an attack

> Cryptography directly supports **Confidentiality** (hiding data) and **Integrity** (verifying data hasn't changed).

---

## Symmetric Encryption

In symmetric encryption, the **same key** is used to both encrypt and decrypt.

- Fast and efficient
- Both parties must share the same secret key
- The challenge: how do you securely share the key in the first place?

### The Caesar Cipher

The Caesar Cipher is one of the oldest and simplest examples of symmetric encryption. It shifts each letter in a message by a fixed number of positions in the alphabet — that number is the key.

**Key = 3 → shift every letter forward 3 positions**

```
A → D    B → E    C → F    ...    X → A    Y → B    Z → C
```

### Encryption Example — `HELLO` with key 3

| Letter | Shifts to |
|--------|-----------|
| H      | K         |
| E      | H         |
| L      | O         |
| L      | O         |
| O      | R         |

```
HELLO  →  KHOOR
```

### Decryption — shift backwards by 3

```
KHOOR  →  HELLO
```

### Why Caesar Cipher Is Weak
- Only 25 possible keys — trivial to brute force
- Vulnerable to frequency analysis (e.g. `E` is the most common letter in English)
- Used today only as a teaching tool, not real security

---

## Asymmetric Encryption

Asymmetric encryption solves the key-sharing problem by using **two mathematically linked keys** instead of one.

### The Two Keys

| Key         | Who Has It         | What It Does                                  |
|-------------|--------------------|-----------------------------------------------|
| Public Key  | Anyone / everyone  | Used to **encrypt** messages to the owner     |
| Private Key | Only the owner     | Used to **decrypt** messages sent to them     |

- Encrypting with a public key → only the private key can decrypt it
- The two keys are linked by complex mathematics
- Recovering the private key from the public key would take an ordinary computer **hundreds to thousands of years**

### How It Works — Alice Sends Bob a Secret Message

```
1. Bob generates a public key and a private key
2. Bob shares his public key with the world (website, key server, etc.)
3. Alice encrypts her message using Bob's public key
4. Alice sends the ciphertext to Bob
5. Bob decrypts it using his private key — only he can read it
```

### Symmetric vs Asymmetric

| Feature        | Symmetric                  | Asymmetric                        |
|----------------|----------------------------|------------------------------------|
| Keys used      | 1 shared key               | 2 keys (public + private)         |
| Speed          | Fast                       | Slower                            |
| Key sharing    | Risky — must share secretly| Safe — public key can be shared openly |
| Best for       | Encrypting large data      | Key exchange, authentication      |
| Examples       | AES, DES                   | RSA, ECC                          |

---

## Takeaways
- The key is always secret — the algorithm doesn't have to be
- The CIA Triad (Confidentiality, Integrity, Availability) underpins all of security
- Symmetric encryption is fast but requires a shared secret key
- The Caesar Cipher is a simple historical example of symmetric encryption
- Asymmetric encryption solves the key-sharing problem using a public/private key pair
- Modern encryption (HTTPS, SSH, email) relies heavily on asymmetric encryption


# Become A Hacker

## Key Topics
- Manual URL enumeration
- Automated directory scanning with Gobuster
- What attackers look for once inside
- Dictionary attacks with Hydra
- Ethical hacking mindset

---

## Manual URL Enumeration

Before using tools, you can manually probe for hidden or unlinked pages by appending common paths to a URL directly in the browser.

**Common paths to check:**

| Path         | What you might find                         |
|--------------|---------------------------------------------|
| `/sitemap`   | A map of all pages on the site              |
| `/mail`      | An internal mail or messaging interface     |
| `/register`  | A user registration page                    |
| `/login`     | An authentication page                      |
| `/admin`     | An admin panel — high value target          |

Example: `http://www.onlineshop.thm/admin`

---

## Automated Directory Scanning — Gobuster

**Gobuster** automates the process of finding hidden pages and directories by brute-forcing URLs from a wordlist.

### Basic Command
```bash
gobuster dir --url http://www.onlineshop.thm/ -w /usr/share/wordlists/dirbuster/directory-list.txt
```

### Flag Breakdown

| Flag / Argument                  | Purpose                                      |
|----------------------------------|----------------------------------------------|
| `dir`                            | Run in directory enumeration mode            |
| `--url http://www.onlineshop.thm/` | Target URL to scan                         |
| `-w /usr/share/wordlists/...`    | Wordlist to use for brute-forcing paths      |

### Tips
- Gobuster is noisy — it generates a lot of requests, easily detected by WAFs/IDS
- Try different wordlists for different results (`common.txt`, `big.txt`, etc.)
- Found pages may be unlinked but still accessible — that's the point

---

## Ethical Hacking Mindset

| Principle               | What It Means                                                                 |
|-------------------------|-------------------------------------------------------------------------------|
| Ask questions           | Don't assume a feature works as intended — ask "what if it doesn't?"         |
| Test the unexpected     | Try inputs and actions the developers didn't consider                         |
| Chain small weaknesses  | A tiny flaw alone may be harmless, but combined with others it can cause damage |
| Think like an adversary | Ask "how would a malicious actor approach this target?"                       |

---

## What Attackers Look for Once Inside

Gaining valid credentials unlocks private areas of an application. Here's what becomes exposed:

| Target                  | Why It's Valuable                                                              |
|-------------------------|--------------------------------------------------------------------------------|
| Sensitive functionality | Modify data, view restricted content, trigger privileged processes             |
| User data               | Names, emails, account details — can be stolen, abused, or sold               |
| Administrative features | Manage users, change settings, gain full control of the application            |
| Further attack surface  | Authenticated access exposes new vulnerabilities to exploit and pivot from     |

---

## Dictionary Attack — Hydra

**Hydra** automates login attempts against a target using a wordlist. It systematically tries each password until one works — this is known as a **dictionary attack**.

### Example Command
```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```

### Flag Breakdown

| Flag / Argument                                           | Purpose                                                        |
|-----------------------------------------------------------|----------------------------------------------------------------|
| `hydra`                                                   | The tool being run                                             |
| `-l admin`                                                | Login with the username `admin`                                |
| `-P passlist.txt`                                         | Use this file as the password list                             |
| `www.onlineshop.thm`                                      | Target website                                                 |
| `http-post-form`                                          | Indicates the login uses an HTTP POST request                  |
| `"/login:username=^USER^&password=^PASS^:F=incorrect"`    | Login path, parameter format, and failure string to detect     |
| `-V`                                                      | Verbose — prints every attempt to the terminal                 |

### How the Form String Works
```
"/login : username=^USER^&password=^PASS^ : F=incorrect"
   ↑              ↑                              ↑
 URL path    Parameters (^USER^/^PASS^ get     Failure string —
             replaced with each attempt)       if this appears in the
                                               response, it failed
```

### Key Concepts

- **Dictionary attack** — tries passwords from a predefined list (not every possible combo)
- **Brute force** — tries every possible combination (slower, noisier)
- **Wordlists** — files like `rockyou.txt` contain millions of common/leaked passwords
- Hydra supports many protocols: HTTP, SSH, FTP, SMB, and more

---

## Typical Attack Flow

```
1. Find hidden pages      →  Gobuster / manual enumeration
2. Locate a login page    →  /login, /admin
3. Identify a username    →  source code, error messages, enumeration
4. Run Hydra              →  dictionary attack against the login form
5. Gain access            →  explore sensitive functionality, data, admin features
6. Chain vulnerabilities  →  pivot deeper into the application
```

---

## Takeaways
- Always check for common paths manually before reaching for tools
- Gobuster automates what would take hours to do manually
- Credentials are a high-value target — they unlock private functionality
- Hydra is the go-to tool for automating login attacks with a wordlist
- Small findings chain together — an exposed `/admin` page plus a weak password is a full compromise
- Always have written permission before running any of these tools


# Become A Defender

## Key Topics
- The defender's core questions
- What defenders can do (Prevention → Response)
- Key infrastructure components and their risks
- Core defender principles

---

## Thinking Like a Defender — The City Analogy

| Defensive Question               | City Analogy                          | Security Equivalent                          |
|----------------------------------|---------------------------------------|----------------------------------------------|
| What are you protecting?         | Homes, buildings, people              | Servers, data, workstations, users           |
| Can you see what you're protecting? | Cameras, reports, patrols          | Logs, network traffic, alerts                |
| What classifies suspicious behaviour? | Locked door attempts, circling cars | Repeated logins, unusual IP addresses    |
| How do you stop a threat?        | Police, blocked roads, curfews        | Firewall rules, IP blocking                  |

---

## What Can You Do as a Defender?

| Action         | What It Means                                                                                  |
|----------------|-----------------------------------------------------------------------------------------------|
| **Prevention** | Put controls in place to stop attacks before they happen — firewalls, antivirus, patching     |
| **Detection**  | Monitor systems and networks to spot suspicious activity — logs, alerts, security tools       |
| **Mitigation** | Limit damage during an incident — block traffic, isolate systems, disable compromised accounts|
| **Analysis**   | Investigate what happened, how, and what was affected — review logs and evidence              |
| **Response**   | Recover from the incident and improve defences to reduce the risk of it happening again       |

---

## Infrastructure Components

### What Each Component Does

| Component        | Purpose                                               | City Analogy             |
|------------------|-------------------------------------------------------|--------------------------|
| Employee Devices | Where users work and access company resources         | Homes                    |
| Web Server       | Hosts websites or applications for users              | Shops / public buildings |
| Mail Server      | Sends and receives email for the organisation         | Post office              |
| Firewall         | Controls what traffic is allowed in or out            | City gate                |
| Internet         | External networks outside your control                | Everything outside the city |

### What Could Go Wrong — and How to Defend It

| Component        | What Could Go Wrong                                      | Defences                                          |
|------------------|----------------------------------------------------------|---------------------------------------------------|
| Employee Devices | User clicks a bad link or downloads malicious software   | Antivirus, regular software updates               |
| Web Server       | Attackers attempt to break into or exploit the site      | Allow only safe traffic, use HTTPS/TLS            |
| Mail Server      | Malicious or deceptive emails reach users                | Spam filters, scan attachments                    |
| Firewall         | Unauthorised external traffic tries to break through     | Strict firewall rules, block known bad IPs        |
| The Internet     | External threats originate here                          | Restrict inbound traffic, monitor for anomalies   |

---

## Key Defender Principles

### Threat Anticipation
- Review the systems you protect and ask **"What if?"**
- Imagine realistic paths an attacker could take to reach their goal
- Think like the attacker to find gaps before they do

### Attack Awareness
- Attacks follow recognisable stages — learn common attack chains and frameworks
- Frameworks like **MITRE ATT&CK** and **Cyber Kill Chain** map attacker behaviour
- Knowing the playbook helps you spot and interrupt attacks early

### Risk Prioritisation
- Not every system carries equal risk
- Identify and focus on **high-value targets** first — domain controllers, databases, mail servers
- A breach of low-value system is far less damaging than a breach of a core server

### Continuous Adaptation
- Defence is **not a one-time setup**
- Threats evolve, techniques change, new vulnerabilities emerge constantly
- Regularly review, test, and update your defences

---

## The Defensive Cycle

```
Anticipate Threats
       ↓
   Prevent Attacks
       ↓
   Detect Activity
       ↓
  Mitigate Damage
       ↓
  Analyse the Incident
       ↓
  Respond & Improve
       ↑_____________|
```

---

## Takeaways
- Defensive security is about protecting, detecting, and responding — not just blocking
- Every component in your infrastructure is a potential attack surface
- The city analogy is a useful mental model — know your gates, your homes, and your patrols
- Good defenders think like attackers — anticipate before reacting
- Security is a continuous process, not a one-time configuration
