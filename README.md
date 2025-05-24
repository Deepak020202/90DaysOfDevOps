
Task 1:-
Understand OSI & TCP/IP Models Learn about the OSI and TCP/IP models, including their layers and purposes. Task: Write examples of how each layer applies to real-world scenarios (e.g., HTTP at the Application Layer, TCP at the Transport Layer).
---
**Solution:-**

![OSI](https://github.com/user-attachments/assets/baa88c4d-0db1-45e3-8f82-f30250ebc886)

Both the OSI and TCP/IP models define how data travels over a network. The OSI model is more theoretical, while the TCP/IP model is more practical and widely used.
## 1. OSI MODEL Overview (7 Layers) 📊 
The OSI (Open Systems Interconnection) model has 7 layers, each with a specific role in data communication.
---
**Layer 7: Application Layer**

Purpose: Provides network services to end-users.

Examples: HTTP (web browsing), FTP (file transfer), SMTP (email).

Real-World Example: When you type www.google.com in your browser, the Application Layer uses HTTP to request the webpage.

**Layer 6: Presentation Layer**

Purpose: Translates data between the application and the network, ensuring data formats are readable by both sender and receiver. It also handles encryption and compression.

Real-World Example: When you watch a video on YouTube, this layer decompresses the video format for smooth playback.

**Layer 5: Session Layer**

Purpose: Establishes, manages, and terminates communication sessions.

Real-World Example: When you're on a Zoom call, the Session Layer keeps the session active and synchronized between you and the other participants.

**Layer 4: Transport Layer**

Purpose: Ensures reliable data delivery, error checking, and flow control. It breaks data into packets and reassembles them at the destination.

Real-World Example: When downloading a file, TCP ensures all parts are received in the correct order.

**Layer 3: Network Layer**

Purpose: Handles routing of data packets and logical addressing (IP addresses).

Real-World Example: When you send a message from Mumbai to New York, this layer determines the best route across multiple networks and routers.

**Layer 2: Data Link Layer**

Purpose: Ensures reliable data transfer across the physical network link. It handles error detection and MAC (Media Access Control) addresses.

Real-World Example: When your laptop connects to Wi-Fi, this layer manages the connection between your device and the router using MAC addresses.

**Layer 1: Physical Layer**

Purpose: Deals with the physical transmission of raw data bits over network cables, radio signals, or fiber optics.

Real-World Example: The Ethernet cable or Wi-Fi radio waves that connect your device to the internet.

---
## 2. TCP/IP Model Overview📊
The TCP/IP model has **4 layers** 
The TCP/IP (Transmission Control Protocol/Internet Protocol) model is more practical and maps roughly to the OSI model but with 4 layers.
---
**Layer 1: Network Access Layer**

Purpose: Handles hardware connections and physical data transmission.

Real-World Example: When you connect to Wi-Fi, this layer manages data transmission through radio waves.

**Layer 2: Internet Layer**

Purpose: Handles logical addressing and routing.

Real-World Example: When sending a WhatsApp message, this layer assigns IP addresses and decides the route.

**Layer 3: Transport Layer**

Purpose: Ensures reliable data transfer, error checking, and flow control by using TCP & UDP protocol.

Real-World Example: During a file download, TCP ensures all parts are received correctly.

**Layer 4: Application Layer**
Purpose: Interfaces with the end-user, managing application services.
Real-World Example: When browsing the web, HTTP in this layer requests and displays webpages.

---

Task 2:-
Protocols and Ports for DevOps Study the most commonly used protocols (e.g., HTTP, HTTPS, FTP, SSH, DNS) and their port numbers. Create a blog, article, GitHub page, or README listing these protocols and explaining their relevance to DevOps workflows.
---

**Solution :-**

protocols enable communication between servers, applications, and services. Let's explore the most commonly used protocols in DevOps workflows.

---
**1. HTTP (Hypertext Transfer Protocol)**

Purpose: Used for transferring web pages and resources over the internet.

Example: Accessing a website via http://example.com. 

**2. HTTPS (Hypertext Transfer Protocol Secure) 🔒**

Purpose: Secure version of HTTP using SSL/TLS encryption.

Example: Accessing a secure website via https://example.com 

![HTTPSdrawio-660x368](https://github.com/user-attachments/assets/d3d7fb1f-d334-4076-a13c-984b2e49fec3)

---
**3. FTP (File Transfer Protocol)**

Purpose: Transfers files between client and server.

Example: Uploading files to a remote server using an FTP client

![File-Transfer-Protocol-and-HTTPS-gif-2](https://github.com/user-attachments/assets/1b9678ec-ecb0-4e12-aac6-ab04dcb6b0c4)
---
**4. SSH (Secure Shell) 🔑**

Purpose: Provides secure remote access and command execution on servers.

Example: Connecting to a remote server using ssh user@hostname

![SSH_](https://github.com/user-attachments/assets/713fd955-a0a0-479d-8ab9-5fa330aafe16)

---
**5. DNS (Domain Name System) 🌐**

Purpose: Translates human-readable domain names to IP addresses.

Example: Resolving example.com to its corresponding IP address.

![DNS](https://github.com/user-attachments/assets/5e9d5f63-ba49-4ea2-b1b5-17326a6aa9cb)
---

**Port Numbers**

port numbers are crucial for communication between devices. They help identify specific processes or services on a device, allowing data to be sent to the correct application. Think of them as apartment numbers in a building – they ensure that the right information reaches the right place.

![PORT_NUMBERS](https://github.com/user-attachments/assets/3cefe6cc-7df0-48fc-a5c0-f72c02fde3ab)
---

**Task 3:-**
AWS EC2 and Security Groups Launch an AWS EC2 instance (free tier is fine). Learn about Security Groups, their rules, and their significance in securing cloud instances. 
Task: Write a step-by-step guide or blog on how to create and configure Security Groups.
---

**Solution :-**

1.Creating Security Groups :- 
Security Groups are a critical part of securing your EC2 instances.

![image](https://github.com/user-attachments/assets/cfc7cf15-3cb0-48dd-a156-3235ceb7c257)
---
2.It act as a virtual firewall to control the inbound and outbound traffic to your EC2 instances

.![image](https://github.com/user-attachments/assets/170d4bef-7430-495a-91be-aad1e636ad69)
---
2.if you allow inbound traffic on a port, the corresponding outbound traffic is automatically allowed.

![image](https://github.com/user-attachments/assets/9e86f9e9-a667-4498-b648-64833a0dff95)
---
**Task 4:-**
Hands-On with Networking Commands Practice essential networking commands like:
ping (check connectivity) traceroute / tracert (trace packet routes) netstat
(network statistics) curl (make HTTP requests) dig / nslookup (DNS lookup)
---

**Solution :-**
**1. ping**

Purpose: Checks connectivity between your device and a remote host. It sends ICMP (Internet Control Message Protocol) Echo Request packets and listens for Echo Reply packets.

Example:

`ping google.com`


---
**2. traceroute / tracert**

Purpose: Traces the route packets take to reach a destination. This helps in identifying network congestion or routing issues.

Example:

`traceroute google.com`

---
**3. netstat**

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
