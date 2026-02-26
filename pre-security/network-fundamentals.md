# Intro to LAN

## Key Topics
- Local Area Networks (LAN)
- Private IP addressing
- Basic LAN components
- Network segmentation concepts

## Takeaways
- Understanding LAN design is essential for network security
- Network structure affects attack surface and defense

# OSI Model

## What I Learned
- All OSI layers and their roles 
- Physical → Data Link → Network → Transport → Session → Presentation → Application

# Frames & Packets

## Frames vs Packets
- Frame (L2): Uses MAC addresses, stays inside the LAN
- Packet (L3): Uses IP addresses, moves between networks
- Frames change at every hop, packets stay mostly the same

## TCP/IP (Three-Way Handshake)
- SYN: Client asks to connect
- SYN-ACK: Server agrees
- ACK: Connection established
- Reliable, ordered, slower

## UDP/IP
- No connection, no handshake
- Fast but unreliable
- No retransmissions or order
- Used for DNS, streaming, games


# Extending my network

## Firewall

A firewall is a security device that controls network traffic based on:
- Source and destination
- Port number
- Protocol (TCP, UDP)

### Types of Firewalls
- **Stateful firewall:** Tracks active connections and inspects traffic in context  
- **Stateless firewall:** Uses fixed rules and evaluates packets individually

---

## VPN (Virtual Private Network)

A VPN allows external devices to securely communicate with internal network resources
by creating an encrypted tunnel between them.

### Benefits
- Encryption protects data in transit
- Improves privacy
- Makes tracking more difficult

### Common VPN Technologies
- PPP
- PPTP
- IPsec







