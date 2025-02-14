---
Task :-
Understand OSI & TCP/IP Models Learn about the OSI and TCP/IP models, including their layers and purposes. Task: Write examples of how each layer applies to real-world scenarios (e.g., HTTP at the Application Layer, TCP at the Transport Layer).

Solution:-
---
![OSI](https://github.com/user-attachments/assets/baa88c4d-0db1-45e3-8f82-f30250ebc886)

Both the OSI and TCP/IP models define how data travels over a network. The OSI model is more theoretical, while the TCP/IP model is more practical and widely used.
## 1. OSI MODEL Overview (7 Layers) 📊 
The OSI (Open Systems Interconnection) model has 7 layers, each with a specific role in data communication.

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

