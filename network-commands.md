# Linux Networking Commands



---

## ping

### What is ping used for?
ping is used to **check basic network connectivity** between your system and another host.

It only checks:
- Is the host reachable?
- What is the network latency?

---

### Which protocol does ping use?
- ICMP (Internet Control Message Protocol)

---

### Does Security Group / Firewall need to be opened?
- YES, ICMP must be allowed
- In cloud (AWS), SG must allow **ICMP**
- No port number is involved

---

### Example Usage
ping google.com  
→ Checks if google.com is reachable

ping -c 4 google.com  
→ Sends only 4 packets

---

### Success Response
64 bytes from 142.250.xx.xx: icmp_seq=1 ttl=117 time=18 ms  
→ Host is reachable

---

### Failure Response
ping: connect: Network is unreachable  
or  
Request timeout  
→ Network, routing, or ICMP blocked

---

## curl

### What is curl used for?
curl is used to **check application or API access** from the terminal.

It checks:
- Port reachability
- Application response (HTTP/HTTPS)

---

### Which protocol does curl use?
- HTTP / HTTPS (TCP-based)

---

### Does Security Group / Firewall need to be opened?
- YES
- The application port (e.g., 80, 443, 8080) must be open
- Firewall and SG must allow TCP traffic

---

### Example Usage
curl http://ip:port  
curl http://example.com  

---

### Success Response
HTTP/1.1 200 OK  
→ Application is reachable and working

---

### Failure Response
Connection refused  
→ App not running or port closed  

Connection timed out  
→ SG / firewall blocking the port

---

### Common curl Options
curl -i http://ip:port  
→ Show headers + status code  

curl -v http://ip:port  
→ Verbose output (DNS, TLS, connection)

---

## nslookup

### What is nslookup used for?
nslookup is used to **check DNS resolution** (domain → IP).

It does NOT check application or port connectivity.

---

### Which protocol does nslookup use?
- DNS (UDP port 53, sometimes TCP)

---

### Does Security Group / Firewall need to be opened?
- Usually NO for outbound
- DNS server must be reachable

---

### Example Usage
nslookup google.com  

---

### Success Response
Name: google.com  
Address: 142.250.xx.xx  
→ DNS resolution is working

---

### Failure Response
NXDOMAIN  
or  
connection timed out  
→ DNS issue or DNS server unreachable

---

## telnet

### What is telnet used for?
telnet is used to **check if a specific port is reachable** on a server.

It does NOT validate application logic.

---

### Which protocol does telnet use?
- TCP

---

### Does Security Group / Firewall need to be opened?
- YES
- Target port must be open in:
  - Security Group
  - Server firewall

---

### Example Usage
telnet server_ip 8080  

---

### Success Response
Connected to server_ip  
→ Port is open and reachable

---

### Failure Response
Connection refused  
→ Service not running  

Connection timed out  
→ Port blocked by SG / firewall

---

## netstat / ss

### What are netstat / ss used for?
They are used to **check which ports are open and which process is using them** (server-side).

---

### Which protocol do they work with?
- TCP and UDP (local system inspection)

---

### Does Security Group / Firewall matter?
- NO (local command)
- Used on the server to confirm listening ports

---

### Example Usage
netstat -tulnp  
ss -tulnp  

---

### Success Output
LISTEN 0 128 0.0.0.0:8080  
→ Application is listening on port 8080

---

### Failure Case
Port not listed  
→ Application not running or wrong port

---

## traceroute

### What is traceroute used for?
traceroute shows the **network path (hops)** taken to reach a destination.

---

### Which protocol does traceroute use?
- ICMP / UDP (depends on OS)

---

### Does Security Group / Firewall need to be opened?
- ICMP or UDP must be allowed
- Often partially blocked in production

---

### Example Usage
traceroute google.com  

---

### Use Case
- Identify where traffic is getting blocked
- Debug latency issues

---

## nc (netcat)

### What is nc used for?
nc is used to **test port connectivity** quickly.

---

### Which protocol does nc use?
- TCP or UDP (depending on options)

---

### Does Security Group / Firewall need to be opened?
- YES
- Target port must be allowed

---

### Example Usage
nc -zv server_ip 80  

---

### Success Response
Connection to server_ip 80 succeeded  
→ Port is open

---

### Failure Response
Connection timed out  
→ Port blocked or unreachable

---

## Interview Debug Flow (VERY IMPORTANT)

When connectivity fails, always think in this order:

1. ping → host reachable?
2. nslookup → DNS working?
3. telnet / nc → port open?
4. ss / netstat → app listening?
5. curl → app responding?

---

## Key Takeaways (MEMORIZE)
- ping → ICMP, no ports
- nslookup → DNS only
- telnet / nc → port reachability
- curl → port + application
- ss / netstat → server-side verification
- Security Group / firewall rules matter for ALL port-based checks
