#### Lab 04: Ping & Traceroute (ICMP)

#### Goal
Use `ping` and `traceroute` to observe ICMP echo requests, echo replies, and Time-to-live (TTL) exceeded messages across network hops.

#### Setup and Commands
* **Workstation VM:** Kali Linux (`10.0.2.4`)
* **Local Target VM:** Metasploitable 2 (`10.0.2.5`)
* **External Target:** `example.com` (`172.66.147.243`)
* **Commands executed:**
```bash
sudo tcpdump -i eth0 -w ping-traceroute.pcap icmp
ping -c 4 10.0.2.5
traceroute -I example.com
```

#### What I Saw
* **Ping (`10.0.2.4` -> `10.0.2.5`):** Wireshark captured four pairs of ICMP Echo (ping) request (Type 8) and Echo (ping) reply (Type 0) packets between Kali and Metasploitable 2.
* **Traceroute Hops (`example.com`):** As `traceroute -I` sent ICMP probes with incrementing TTL values (`TTL=1`, `TTL=2`, etc.), intermediate routers (such as the gateway `10.0.2.1`) decremented the TTL to zero and returned ICMP Time-to-live exceeded in transit (Type 11, Code 0) messages until the probe reached `example.com` (`172.66.147.243`), which responded with Echo (ping) replies.
* **Security Hygiene:** Verified that only private NAT addresses (`10.0.2.x`) and public destination IPs appeared in the capture, ensuring no sensitive host/ISP IP addresses were exposed.

#### What I Learned
I learned how `ping` verifies host reachability using ICMP Echo messages (Types 8 and 0), and how `traceroute` maps each router hop along a path by intentionally triggering ICMP Time-to-live exceeded (Type 11) responses.
