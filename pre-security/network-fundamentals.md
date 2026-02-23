	# Intro to LAN
	
## Key Topics
- Local Area Networks (LAN)
- Private IP addressing
- Basic LAN components
- Network segmentation	 concepts

## Takeaways
- Understanding LAN design is essential for network security
- Network structure affects attack surface and defense

	# OSI model

## What i learned 
all the layers in the osi model and their job
physical -> data link -> network -> transport -> session -> presentation -> application

	
	# Frames & Packets	

## Frames vs Packets
- Frame (L2): Uses MAC addresses, stays inside the LAN
- Packet (L3): Uses IP addresses, moves between networks
- Frames change at every hop, packets stay mostly the same

## TCP/IP (three way handshake)
- SYN: Client asks to connect
- SYN-ACK: Server agrees
- ACK: Connection established
- Reliable, ordered, slower

## UDP/IP
- No connection, no handshake
- Fast but unreliable
- No retransmissions or order
- Used for DNS, streaming, games

