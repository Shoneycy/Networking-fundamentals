#### Lab 03: DNS Resolution

#### Goal
Capture and inspect DNS queries and responses over UDP port 53 to observe how domain names resolve into A and MX records.

#### Setup and Commands
* **Workstation VM:** Kali Linux (`10.0.2.4`)
* **DNS Resolver:** `10.74.113.145`
* **Commands executed:**
```bash
sudo tcpdump -i eth0 -w dns-lookup.pcap udp port 53
dig example.com
dig example.com MX
```

#### What I Saw
* **DNS Queries & Responses:** In Wireshark, Kali (`10.0.2.4`) sent standard recursive DNS queries over UDP port 53 to the DNS resolver (`10.74.113.145`) for `example.com` (`A` and `MX` record types) and received matching responses tracked by Transaction ID.
* **A Record Answer:** Resolved `example.com` to the IPv4 address `172.66.147.243` along with its Time to Live (TTL) caching value in the Answers section.
* **MX Record Answer:** Returned a null mail exchange record (`0 .`, per RFC 7505, indicating the domain does not accept email) along with its TTL value.

#### What I Learned
I learned how DNS translates human-readable domain names into IP addresses over UDP port 53, and how to inspect record types (`A` vs. `MX`), TTL values, and answering servers inside Wireshark.
