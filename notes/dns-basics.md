# DNS Basics (Domain Name System)
DNS acts as the phonebook of the internet, translating human-readable domain names (like example.com) into machine-readable IP addresses. 
How a DNS Lookup Works
Query:A client sends a DNS request—usually over UDP port 53—asking for the IP address of a domain.
Recursive Resolver:Your configured DNS server checks its cache. If it doesn't know the answer, it queries root, Top-Level Domain (.com), and authoritative name servers on your behalf.
Response:The server returns the matching record along with a TTL (Time to Live) value, which tells your computer how many seconds it can cache the answer before asking again.
Common DNS Record Types
A Record:Maps a domain name to an IPv4 address.
AAAA Record:Maps a domain name to an IPv6 address.
MX (Mail Exchange) Record:Directs email to the mail servers responsible for a domain.
CNAME (Canonical Name) Record:Points one domain name (an alias) to another domain name.
NS (Name Server) Record:Identifies the authoritative DNS servers for a domain.
