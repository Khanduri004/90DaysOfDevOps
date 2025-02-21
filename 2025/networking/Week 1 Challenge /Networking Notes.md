# Week 1: Networking Challenge

# 1🌍 OSI & TCP/IP Models - A DevOps Perspective  

📌 **Overview**  
The **OSI (Open Systems Interconnection) model** and the **TCP/IP (Transmission Control Protocol/Internet Protocol) model** are both conceptual frameworks used to understand network communication. While the OSI model has seven layers and is more theoretical, the TCP/IP model has four layers and is more practical, being the basis for the Internet's architecture. Let’s break both models down:
---
# 1. OSI Model:
The OSI model consists of seven layers, from top to bottom:

**Application Layer (Layer 7)**:

**Purpose**: This is where end-user software (such as web browsers, email clients, and FTP clients) interacts with the network. It deals with network services that directly support applications.
**Protocols**: HTTP, FTP, DNS, SMTP, POP3.
 
 **Presentation Layer (Layer 6)**:

**Purpose**: It ensures that data is in a readable format. It may involve data compression, encryption, or translation between different data formats (e.g., from ASCII to EBCDIC).
**Protocols**: SSL/TLS, JPEG, GIF.

**Session Layer (Layer 5)**:

**Purpose**: This layer manages and controls the dialogue (sessions) between two devices. It ensures that the session is opened, maintained, and properly closed.
**Protocols**: NetBIOS, RPC, SMB.

**Transport Layer (Layer 4)**:

**Purpose**: Provides reliable data transfer. It ensures that data is delivered error-free, in sequence, and without losses or duplications.
**Protocols**: TCP, UDP.

**Network Layer (Layer 3)**:

**Purpose**: Responsible for logical addressing, routing, and packet forwarding. It manages how data is sent across networks and routes packets to the correct destination.
**Protocols**: IP, ICMP, IGMP, IPsec.
 
 **Data Link Layer (Layer 2):**

**Purpose:** This layer is responsible for the physical addressing and error detection/correction on the link. It also controls access to the physical medium.
**Protocols:** Ethernet, PPP, Frame Relay.

**Physical Layer (Layer 1):**

**Purpose:** Concerned with the transmission of raw bits over a physical medium. This layer defines the hardware elements like cables, switches, and wireless signals.
**Protocols:** Ethernet cables, fiber optics, radio frequencies.

# 2. TCP/IP Model:

The **TCP/IP model** is a more practical and widely used model that consists of four layers. It maps loosely to the OSI model but is simplified for real-world usage:

**Application Layer:**

**Purpose**: Corresponds to the top three layers of the OSI model (Application, Presentation, and Session). It provides network services directly to end-users, handling high-level protocols, data encoding, and session management.
**Protocols**: HTTP, FTP, DNS, SMTP, POP3.

**Transport Layer:**

**Purpose**: Ensures end-to-end communication reliability. It manages flow control, error checking, and data retransmission.
**Protocols**: TCP, UDP.

**Internet Layer:**

**Purpose:** Handles logical addressing, routing, and packet forwarding, similar to the Network Layer of the OSI model.
**Protocols**: IP, ICMP, IGMP.

**Network Access Layer:**

**Purpose**: Combines the OSI's Data Link and Physical layers. It deals with physical transmission and access to the network medium.
**Protocols**: Ethernet, ARP, PPP, Frame Relay.

**Comparison Between OSI and TCP/IP Models:**

**Layer Count:** OSI has 7 layers, while TCP/IP has 4.
**Purpose:** OSI is more theoretical, while TCP/IP is practical and aligned with the internet.
**Layer Mapping:** TCP/IP combines the OSI’s Session, Presentation, and Application layers into one layer.

## 📊 OSI Model (7 Layers) - "Think of it Like a Postal System"  

Real-Life Workflow Summary (for accessing a website):

**1)** Your browser sends a request to access www.example.com (Application Layer).

**2)** DNS resolution: The browser queries DNS to translate www.example.com into an IP address (Application Layer).

**3)** The data is split into packets using TCP and sent to the IP address (Transport and Internet Layers).

**4)** The packets are transmitted over your local network (Network Access Layer), either via Ethernet or Wi-Fi.

**5)** Data packets are routed over the internet through various routers and networks (Network Layer).

**6)** The server receives the data, processes the request, and sends back the webpage content (repeating steps in reverse).

**7)** The browser reassembles the data and displays the website (Presentation Layer).

This process highlights how both the OSI and TCP/IP models work in tandem, each layer contributing its part to ensure smooth communication between devices over a network.

---
---

## 🌟 Real-World Examples in DevOps & Cloud Computing  

🔹 **Application Layer (HTTP/HTTPS)**
   - Web applications running on **AWS EC2 instances** use HTTP(S) for API requests.
   - **Load balancers** forward traffic to different backend servers based on HTTP headers.  

🔹 **Transport Layer (TCP/UDP)**
   - **TCP** ensures reliability in file transfers using **SCP, FTP, and SSH**.
   - **UDP** is used in **Kubernetes service discovery** for DNS resolution.  

🔹 **Network Layer (IP Routing)**
   - **AWS VPC (Virtual Private Cloud)** allows **custom IP addressing** for EC2 instances.
   - DevOps teams **route traffic** across AWS regions using **VPC Peering**.  

🔹 **Data Link Layer (MAC Addresses & Ethernet)**
   - **Docker networking** uses **bridge networks** to connect containers.  

🔹 **Physical Layer (Hardware Communication)**
   - **AWS Direct Connect** provides a dedicated fiber link between on-premises & AWS.  


## 🎯 Why Understanding OSI & TCP/IP Models is Important in DevOps?  
✅ Helps troubleshoot **networking issues** in **Kubernetes, AWS, and CI/CD pipelines**.  
✅ Guides **firewall, security groups, and IAM role configurations**.  
✅ Essential for **load balancing, container networking, and API management**.  



## 🎯 **Final Step: Publish & Share!**  

 **Project Repository:** [90 Days of DevOps - Networking]📌 
    https://github.com/Khanduri004/90DaysOfDevOps/edit/Personal-Notes/2025/networking/Week%201%20Challenge%20/Networking%20Notes.md

 **Contributions are welcome! Feel free to raise an issue or PR.**  

 **Task Completed!** Happy Learning! 🎉

