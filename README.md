#### Networking-fundamwntals
Hands-on packet  captue and protocol analysis labs conducted in a virtualized kali linux environment using tcpdump and wireshark 
rather than relying on automated scanning tools,this reository focuses on generating raw network traffic and inspecting how core protocols behave at packet level.
#### Repository structure 
* **notes/**-conceptual summaries  of the  TCP/IP model and DNS resolution.
* **labs/01-tcp-handshake/-** capturing and analyzing the tcp three way  handshake(SYN,SYN-ACK,ACK)
* **labs/02-open-vs-closed-ports/-** comparing  how a target responds to open(SYN-ACK) vs closed (RST) ports.
* **labs/o3-dns/-** Inspecting DNS queries,responses,record types,and TTL values.
* **labs/04-ping-traceroutes/-** analyzing ICMP echo requests/reolies and tracing network hops
#### Lab Environment & Tools
* **Virtual Machines:** Kali linux(workstation) and Metasploitable 2(target) on an  isolated virtual network.
* **Packet Captures & Analysis:** tcpdump,wireshark
* **Networking utilities:** curl,netcat,dig,ping,traceroute
