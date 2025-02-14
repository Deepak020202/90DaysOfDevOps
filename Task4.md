**Task :-**
Hands-On with Networking Commands Practice essential networking commands like:
ping (check connectivity) traceroute / tracert (trace packet routes) netstat
(network statistics) curl (make HTTP requests) dig / nslookup (DNS lookup)
---

**Solution :-**
**1. ping**

Purpose: Checks connectivity between your device and a remote host. It sends ICMP (Internet Control Message Protocol) Echo Request packets and listens for Echo Reply packets.

Example:
`ping google.com`
This checks if you can reach Google's servers and measures the time it takes for packets to travel.

---
**2. traceroute / tracert**

Purpose: Traces the route packets take to reach a destination. This helps in identifying network congestion or routing issues.

Example:
`traceroute google.com`

---
3. netstat
Purpose: Displays network statistics, including active connections, routing tables, and network interface statistics.

Example:

`netstat -an`

---
**4. curl**

Purpose: Transfers data to or from a server using various protocols, commonly HTTP/HTTPS. Useful for making web requests and API testing.

Example:

`curl -I https://google.com`

---

**5. dig / nslookup**

Purpose: Performs DNS lookups to query DNS records such as A, MX, and CNAME records.

Example:

`dig google.com`

---
