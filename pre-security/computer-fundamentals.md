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

