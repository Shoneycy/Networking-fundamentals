# The TCP/IP Model
The TCP/IP model explains how data is packaged, addressed, transmitted, and received across a network. It breaks network communication into four practical layers:
 Application Layer
What it does: Provides network services directly to user applications.
Common protocols: HTTP/HTTPS (web), DNS (domain names), SSH (remote login), FTP (file transfer).
Lab connection: Tools like curl and dig operate here when requesting webpages or looking up domain names.
Transport Layer
 What it does: Manages end-to-end communication between devices using port numbers and handles reliability.
 Key protocols:
TCP (Transmission Control Protocol): Connection-oriented and reliable. Uses a three-way handshake (SYN, SYN-ACK, ACK) before sending data (e.g., HTTP on port 80).
UDP (User Datagram Protocol): Connectionless and fast, without handshakes or delivery guarantees (e.g., DNS queries on port 53).
 Internet Layer
What it does: Handles logical addressing (IP addresses) and routes packets across different networks to reach their destination.
Key protocols: IP (IPv4/IPv6) and ICMP (used by ping and traceroute for diagnostics).
Network Access (Link) Layer
What it does: Handles the physical transmission of data over hardware (Ethernet cables, Wi-Fi) using MAC addresses.
