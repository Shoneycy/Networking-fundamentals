#### Lab 01: TCP Handshake

#### Goal
Capture and observe the three-way TCP handshake (SYN, SYN-ACK, ACK) when sending an HTTP request to a web server.

#### Setup and Commands
* **Workstation VM:** Kali Linux (`10.0.2.4`)
* **Target VM:** Metasploitable 2 (`10.0.2.5`)
* **Commands executed:**

```bash
# Terminal 1: Capture HTTP traffic on eth0
sudo tcpdump -i eth0 -w tcp-handshake.pcap tcp port 80

# Terminal 2: Generate HTTP traffic
curl http://10.0.2.5
```

#### Observations
* **Packet 1 (`[SYN]`):** Kali (`10.0.2.4`) sends a TCP SYN packet (`Seq=0`) to Metasploitable (`10.0.2.5`) on port 80 to initiate a connection.
* **Packet 2 (`[SYN, ACK]`):** Metasploitable (`10.0.2.5`) responds with SYN-ACK (`Seq=0, Ack=1`), acknowledging the request and confirming port 80 is open.
* **Packet 3 (`[ACK]`):** Kali (`10.0.2.4`) sends an ACK packet (`Seq=1, Ack=1`) back to complete the three-way handshake, immediately followed by the `HTTP GET` request.

#### Key Takeaways
I learned how to capture live network traffic using `tcpdump` and isolate handshake packets in Wireshark using display filters (`tcp.flags.syn == 1`) and stream tracking (`Follow > TCP Stream`). This verified how TCP establishes a reliable session before transmitting application-layer data.
