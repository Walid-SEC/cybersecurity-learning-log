# PC Hardware & Boot Process

## Key Topics
- Core hardware components and their roles
- How components work together
- The boot process step by step

---

## Core Hardware Components

| Component        | Analogy                  | Purpose                                                        |
|------------------|--------------------------|----------------------------------------------------------------|
| Motherboard      | Skeleton & nervous system| Holds all components in place and connects them together       |
| CPU              | Brain                    | Continuously executes instructions and performs calculations   |
| RAM              | Short-term memory        | Temporarily holds data while the PC is running                 |
| HDD / SSD        | Long-term memory         | Permanently stores data — SSD is significantly faster          |
| PSU              | Heart                    | Supplies electricity to all components                         |
| GPU              | Visual cortex            | Processes and displays visual data to a monitor                |
| Network Adapter  | Ears & mouth             | Allows the computer to communicate with other systems          |

---

## Component Breakdown

### 🧠 CPU (Central Processing Unit)
- The brain of the computer
- Executes all instructions and performs calculations
- Speed measured in GHz (clock speed)
- More cores = better multitasking

### 💾 RAM (Random Access Memory)
- Temporary, fast storage used while the PC is running
- Data is lost when the PC is turned off
- More RAM = smoother multitasking
- Common sizes: 8GB, 16GB, 32GB

### 🗄️ HDD / SSD (Storage)
- Permanently stores your OS, files, and applications
- **HDD** (Hard Disk Drive) — mechanical, slower, cheaper, larger capacity
- **SSD** (Solid State Drive) — no moving parts, much faster, more expensive
- **NVMe SSD** — even faster, plugs directly into the motherboard

### ⚡ PSU (Power Supply Unit)
- Converts mains electricity into usable power for components
- Rated in watts — needs to match the demand of your components
- A failing PSU can cause random shutdowns or hardware damage

### 🖥️ GPU (Graphics Card)
- Receives data from the OS and applications
- Renders and outputs visual data to a monitor
- Essential for gaming, video editing, and 3D rendering
- Has its own dedicated memory (VRAM)

### 🌐 Network Adapter
- Allows the PC to connect to networks and communicate with other systems
- Can be wired (Ethernet) or wireless (Wi-Fi)
- Often built into the motherboard on modern systems

### 🔩 Motherboard
- The central circuit board that everything connects to
- Contains slots for CPU, RAM, GPU, storage, and more
- Manages communication between all components via buses and chipsets

---

## The Boot Process

What happens between pressing the power button and seeing your desktop:

```
Power Button → PSU → UEFI/BIOS → POST → Boot Device → Bootloader → OS
```

### Step by Step

**1. Press Power Button**
- Signal is sent to the PSU to start supplying power
- All components begin receiving electricity

**2. Firmware Starts (UEFI / BIOS)**
- UEFI (modern) or BIOS (legacy) is the first software to run
- Stored on a chip on the motherboard
- Initialises and coordinates hardware components

**3. POST — Power-On Self Test**
- UEFI runs a self-check on all required hardware
- Verifies that components like RAM and CPU are present and functioning
- Errors are reported via beep codes or on-screen alerts

**4. Select Boot Device**
- UEFI checks a priority list of bootable devices
- Typically boots from the SSD or HDD that has the OS installed
- Order can be changed in UEFI settings (useful for booting from USB)

**5. Bootloader Initiates**
- The bootloader (e.g. GRUB on Linux, Windows Boot Manager) is loaded
- Its job is to load the operating system into RAM
- Once done, UEFI hands full control to the OS

**6. OS Loads**
- The operating system takes over
- Drivers, services, and startup programs load
- You reach the login screen or desktop

---

## Takeaways
- Every component has a specific role — understanding them helps with troubleshooting
- The motherboard is the backbone that makes communication between components possible
- SSDs are significantly faster than HDDs — worth knowing for both performance and forensics
- The boot process follows a strict sequence — knowing it helps diagnose startup issues
- UEFI replaced BIOS on modern systems and offers more features and security

# Computer Types

## Key Topics
- Different categories of computers
- Their purpose and typical use cases
- How they differ in power, size, and function

---

## Overview

Not all computers are the same — they come in many forms depending on what they're designed to do.

---

## Computer Types

| Type              | Description                                                                 | Examples                        |
|-------------------|-----------------------------------------------------------------------------|---------------------------------|
| Desktop           | Stationary, high performance, easy to upgrade                               | Gaming PC, office workstation   |
| Laptop            | Portable, built-in screen and battery, less upgradeable                     | MacBook, Dell XPS               |
| Server            | Designed to handle requests from many clients, runs 24/7                    | Web server, file server         |
| Smartphone        | Pocket-sized, touchscreen, mobile OS                                        | iPhone, Android devices         |
| Tablet            | Larger than a phone, touchscreen, portable                                  | iPad, Samsung Galaxy Tab        |
| Embedded Computer | Built into a device to perform one specific task                            | Smart TV, router, microwave     |
| Raspberry Pi / SBC| Small single-board computer, used for projects and learning                 | Raspberry Pi, Arduino           |
| Mainframe         | Extremely powerful, handles massive amounts of data for large organisations | Used by banks, governments      |
| Supercomputer     | The most powerful computers in existence, used for complex simulations      | NASA systems, weather modelling |

---

## Key Differences at a Glance

| Feature       | Personal (Desktop/Laptop) | Server          | Embedded        |
|---------------|---------------------------|-----------------|-----------------|
| User          | Individual                | Many clients    | No direct user  |
| Uptime        | As needed                 | 24/7            | Always on       |
| OS            | Windows, macOS, Linux     | Linux, Windows Server | Custom / none |
| Upgradeable   | Yes (desktop especially)  | Yes             | No              |
| Purpose       | General use               | Serve resources | Single task     |

---

## Takeaways
- The type of computer is defined by its **purpose, power, and portability**
- Servers are just computers optimised to serve many users at once
- Embedded computers are everywhere — your router, smart TV, and car all run them
- In cybersecurity, understanding computer types helps you know what you're targeting or defending


# Client-Server Basics

## Key Topics
- What a client and server are
- How they communicate
- Common examples in the real world

---

## What Is the Client-Server Model?

The client-server model is a way of structuring communication between two parties over a network:

- **Client** — the device or application that *requests* something
- **Server** — the machine that *receives* the request and *sends back* a response

```
Client  ──── request ────►  Server
Client  ◄─── response ───  Server
```

Every time you open a website, send an email, or stream a video — you're a client talking to a server.

---

## Client vs Server

| Feature       | Client                          | Server                          |
|---------------|----------------------------------|---------------------------------|
| Role          | Sends requests                  | Listens for and handles requests|
| Initiates?    | Yes                             | No — waits for clients          |
| Examples      | Browser, mobile app, game       | Web server, database, mail server|
| Location      | User's device                   | Data centre or cloud            |

---

## How They Communicate

1. Client sends a **request** (e.g. `GET /index.html`)
2. Server **processes** the request
3. Server sends back a **response** (e.g. HTML page, data, file)
4. Client **renders or uses** the response

Communication happens over protocols like:
- **HTTP / HTTPS** — web browsing
- **FTP** — file transfers
- **SMTP / IMAP** — email
- **SSH** — secure remote access

---

## Common Real-World Examples

| Scenario              | Client             | Server              |
|-----------------------|--------------------|---------------------|
| Visiting a website    | Your browser       | Web server          |
| Sending an email      | Your email app     | Mail server         |
| Playing online games  | Your game client   | Game server         |
| Using a database app  | Your application   | Database server     |
| Remote terminal access| Your SSH client    | Remote Linux server |

---

## Takeaways
- The client always initiates — the server always listens
- One server can serve many clients at the same time
- Understanding this model is foundational for networking, web dev, and security
- In pentesting, you are often acting as a client probing how a server responds

# Virtualisation, VMs & Containers

## Key Topics
- What virtualisation is and why it matters
- Hypervisors (Type 1 vs Type 2)
- Virtual Machines vs Containers
- Docker basics
- Key terminology

---

## What Is Virtualisation?

Virtualisation enables a **single physical computer to act like multiple separate computers**, allowing multiple apps or operating systems to share the same hardware resources — saving cost, space, and energy.

---

## Hypervisor

The hypervisor is the software that **manages and allocates resources** for each virtual machine.

### What It Does
- Divides one physical machine into multiple virtual ones
- Gives each VM its own share of CPU, memory, and storage
- Keeps each VM isolated and secure from the others
- Manages the full lifecycle of VMs — start, stop, pause, clone, delete

### Type 1 vs Type 2

| Feature        | Type 1 (Bare Metal)                        | Type 2 (Hosted)                          |
|----------------|--------------------------------------------|------------------------------------------|
| Runs on        | Directly on physical hardware              | On top of an existing OS                 |
| Speed          | Fast and efficient                         | Slower (extra layer)                     |
| Best for       | Servers, data centres, production          | Learning, testing, small setups          |
| Examples       | VMware ESXi, Microsoft Hyper-V, Proxmox    | VirtualBox, VMware Workstation           |

### Use Case Reference

| Use Case               | Type 1 | Type 2 |
|------------------------|--------|--------|
| Test malicious files   |        | ✅     |
| Production server      | ✅     |        |
| Database server        | ✅     |        |
| Software testing       |        | ✅     |
| Running Kali Linux     |        | ✅     |
| Data centre            | ✅     |        |

---

## Virtual Machines (VMs)

A VM is a **virtual computer** created and managed by the hypervisor. Even though it's virtual, it behaves exactly like a real machine.

### Key Properties
- Has its own virtual CPU, RAM, storage, and network adapter
- Can run any operating system (Windows, Linux, etc.)
- Completely isolated — if one VM breaks, the others keep running
- Can be snapshotted, cloned, or rolled back

### When to Use a VM
- Running a full separate OS
- Security research (malware analysis in isolation)
- Simulating servers or network environments
- Testing software in a clean environment

---

## Containers

A container is a **lightweight, isolated environment that runs a single application**. Instead of bringing a whole OS like a VM does, it borrows the core of the host system by running on the same **kernel**.

### Key Properties
- Packages the app and all its dependencies (libraries, tools, versions)
- Shares the host OS — starts almost instantly
- Isolated from other containers — one misbehaving container doesn't affect others
- Runs consistently on any machine — great for dev, testing, and deployment

### VM vs Container

| Feature          | Virtual Machine         | Container                  |
|------------------|-------------------------|----------------------------|
| Includes OS?     | Yes — full OS           | No — shares host kernel    |
| Startup time     | Minutes                 | Seconds                    |
| Size             | GBs                     | MBs                        |
| Isolation        | Full                    | Process-level              |
| Best for         | Full system simulation  | Running individual apps    |
| Analogy          | A full apartment        | A room in a shared flat    |

---

## Docker

**Docker** is the most popular platform for building, deploying, and running containers.

- Open-source and widely used in industry
- Uses **container images** — pre-packed templates used to spin up containers
- Makes it easy to deploy containers inside a VM or directly on a host
- One command can spin up an entire app environment

```bash
docker pull ubuntu          # download an image
docker run -it ubuntu bash  # start a container interactively
docker ps                   # list running containers
docker stop <id>            # stop a container
```

---

## Key Terminology

| Term              | Definition                                                               |
|-------------------|--------------------------------------------------------------------------|
| Virtualisation    | Enables one physical machine to act as multiple separate computers       |
| Hypervisor        | The manager software that creates and runs virtual machines              |
| Virtual Machine   | A full virtual computer with its own OS, running inside a real machine   |
| Container         | A lightweight isolated environment for running a single application      |
| Container Image   | A pre-built template/recipe used to create containers                    |
| Network Ports     | Numbered entry points that applications use to communicate over a network|
| Docker            | Open-source platform for building and running containers                 |
| Kernel            | The core of an OS — containers share this with the host                  |

---

## Benefits of Virtualisation

-  **Cost savings** — fewer physical machines needed
-  **Better resource usage** — share hardware efficiently
-  **Safe testing** — isolate malware and experiments from the host
-  **Faster deployment** — spin up environments in minutes
-  **Flexibility & portability** — run anywhere, move easily
-  **Scalability** — spin up more instances on demand
-  **Centralised management** — control everything from one place

---

## Takeaways
- Virtualisation lets one machine do the job of many
- Type 1 hypervisors are for production, Type 2 are for learning and testing
- VMs give you a full isolated OS — containers give you a lightweight isolated app
- Docker is the go-to tool for containerisation
- In cybersecurity, VMs are essential for safely analysing malware and building lab environments

# Cloud Computing

## Key Topics
- What the cloud offers and why it matters
- Types of cloud (Public, Private, Hybrid)
- Cloud service models (IaaS, PaaS, SaaS)
- Major cloud vendors
- Real-world examples

---

## Cloud Benefits & Characteristics

| Benefit              | What It Means                                                                 |
|----------------------|-------------------------------------------------------------------------------|
| Scalability          | Easily scale up or down as your needs change                                  |
| On-demand service    | Spin up or remove servers and storage instantly — no waiting for hardware     |
| Pay as you go        | Charged based on usage, not upfront hardware costs                            |
| Security             | Cloud providers handle infrastructure protection with strong security measures|
| High availability    | Apps keep running even if part of the system fails                            |
| Global access        | Your application is accessible to users anywhere in the world                 |

---

## Types of Cloud

### Public Cloud
- Shared infrastructure managed by a cloud provider
- Affordable, easy to scale, no hardware to manage
- Best for: startups, websites, global apps
- Examples: AWS, Azure, GCP

### Private Cloud
- Dedicated infrastructure for a single organisation
- Greater control, customisation, and compliance
- Best for: banks, healthcare, government — anywhere sensitive data is involved

### Hybrid Cloud
- A mix of public and private cloud
- Sensitive data stays private, but can scale publicly during high demand
- Best for: e-commerce platforms, enterprises with compliance requirements

---

## Cloud Service Models

Think of it as how much the provider manages vs how much you manage:

```
IaaS → PaaS → SaaS
You manage less as you move right
```

### IaaS — Infrastructure as a Service
- You rent virtual servers, storage, and networking
- You manage: OS, middleware, runtime, apps, data
- Provider manages: physical hardware
- Best for: developers who need full control
- Examples: AWS EC2, Azure Virtual Machines

### PaaS — Platform as a Service
- Provider manages infrastructure AND the OS
- You focus on: building, deploying, and running your app
- Best for: developers who don't want to manage servers
- Examples: Heroku, Google App Engine, AWS Elastic Beanstalk

### SaaS — Software as a Service
- Provider manages everything
- You just use the software via a browser or app
- Best for: end users and businesses
- Examples: Gmail, Zoom, Slack, Dropbox

### Quick Comparison

| Model | You Manage              | Provider Manages                    |
|-------|-------------------------|--------------------------------------|
| IaaS  | OS, apps, data          | Hardware, networking                 |
| PaaS  | Apps, data              | Hardware, OS, runtime                |
| SaaS  | Nothing (just use it)   | Everything                           |

---

## Major Cloud Vendors

| Provider           | Known For                                              |
|--------------------|--------------------------------------------------------|
| **AWS**            | Industry leader — most extensive services & global reach |
| **Microsoft Azure**| Strong in enterprise and hybrid cloud environments     |
| **Google Cloud**   | Data analytics, AI, and machine learning tools         |
| **Alibaba Cloud**  | Leading provider in Asia, growing globally             |
| **IBM Cloud**      | Hybrid cloud and AI-driven business solutions          |
| **Oracle Cloud**   | Enterprise applications and databases                  |

> AWS holds the largest market share and is the most widely used platform in the industry.

---

## Real-World Examples

| Company       | How They Use the Cloud                                                               |
|---------------|--------------------------------------------------------------------------------------|
| **Netflix**   | Runs entirely on AWS — scales globally and streams reliably to millions at once      |
| **Spotify**   | Handles millions of songs and users, scales fast when new features drop              |
| **Instagram** | Stores massive amounts of photos/videos and delivers them quickly worldwide          |
| **Online stores** | Handle traffic spikes on Black Friday without buying permanent infrastructure    |

---

## Takeaways
- The cloud removes the need to buy and manage physical hardware
- Public cloud suits most use cases — private cloud is for strict compliance needs
- IaaS, PaaS, and SaaS differ by how much control vs convenience you want
- AWS is the dominant player, but Azure and GCP are strong alternatives
- Even the biggest platforms in the world rely on cloud infrastructure to scale
