#### Lab 02: Open vs. Closed Ports

#### Goal
Compare how a target host responds at the TCP packet level when connecting to an open port (`80`) versus a closed port (`81`).

#### Setup and Commands
* **Workstation VM:** Kali Linux (`10.0.2.4`)
* **Target VM:** Metasploitable 2 (`10.0.2.5`)
* **Commands executed:**

```bash
# Terminal 1: Capture traffic on ports 80 and 81
sudo tcpdump -i eth0 -w open-vs-closed.pcap 'tcp port 80 or tcp port 81'

# Terminal 2: Probe open and closed ports with Netcat
nc -vz 10.0.2.5 80
nc -vz 10.0.2.5 81
```

#### What I Saw
* **Open Port (`80`):** Netcat reported that the connection succeeded. In Wireshark, Kali (`10.0.2.4`) sent a `[SYN]` packet to port 80, and Metasploitable (`10.0.2.5`) replied with **`[SYN, ACK]`**, confirming port 80 is open and listening. Kali then completed the handshake and immediately closed the session.
* **Closed Port (`81`):** Netcat reported `Connection refused`. In Wireshark, Kali sent a `[SYN]` packet to port 81, and Metasploitable immediately replied with **`[RST, ACK]`** (Wireshark filter: `tcp.flags.reset == 1`), actively rejecting the connection.

#### What I Learned
I learned how TCP flags reveal port states at the packet level—the exact mechanism tools like Nmap rely on during a TCP SYN scan:
* **Open port:** Replies with `SYN-ACK`.
* **Closed port:** Replies with `RST-ACK`.
