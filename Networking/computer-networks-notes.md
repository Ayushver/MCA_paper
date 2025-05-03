# Easy-to-Understand Computer Networks Notes

## What You'll Learn
1. [What Are Computer Networks](#what-are-computer-networks)
2. [How Networks Are Built](#how-networks-are-built)
3. [The Physical Layer - Cables and Signals](#the-physical-layer)
4. [The Data Link Layer - Getting Data Across One Link](#the-data-link-layer)
5. [The Network Layer - Finding Paths Across Networks](#the-network-layer)
6. [The Transport Layer - End-to-End Communication](#the-transport-layer)
7. [The Application Layer - What Users See](#the-application-layer)
8. [Keeping Networks Safe](#keeping-networks-safe)
9. [Wireless Networks](#wireless-networks)
10. [New Network Technologies](#new-network-technologies)

## What Are Computer Networks

### The Basics
A computer network is simply a group of computers and devices connected together. When devices are networked, they can talk to each other, share files, and use the same equipment like printers or internet connections.

Think of a network like a neighborhood where houses (computers) are connected by streets (cables or wireless signals) and everyone can visit each other or share things.

### Why We Use Networks
- **Sharing stuff**: Everyone can use the same printer or access the same files
- **Talking to each other**: Sending messages, emails, or video calls
- **Using the internet together**: One internet connection can be shared by many people
- **Working together**: Many people can work on the same project or document
- **Saving money**: Buying one printer for the whole office is cheaper than buying one for each person

### Types of Networks by Size

#### Very Small Networks (PAN - Personal Area Network)
- Just around one person (about 10 meters or 33 feet)
- Examples: 
  - Your phone connected to your wireless earbuds
  - Your laptop connected to a Bluetooth mouse
  - Your smartwatch connected to your phone

![PAN Example](https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/Personal_Area_Network.svg/640px-Personal_Area_Network.svg.png)

#### Small Networks (LAN - Local Area Network)
- Inside one building or a small group of buildings
- Examples:
  - All the computers in your school or office
  - The devices in your home (home network)
  - Computers in a university lab

![LAN Example](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d0/LAN_Network_diagram.svg/500px-LAN_Network_diagram.svg.png)

#### City-Sized Networks (MAN - Metropolitan Area Network)
- Covers a city or large campus
- Examples:
  - A university with many buildings
  - City government connecting all offices
  - Cable TV network in a city

#### Big Networks (WAN - Wide Area Network)
- Covers countries or the whole world
- The internet is the biggest WAN
- Examples:
  - A company with offices in different cities
  - Banks connecting all their branches
  - The internet connecting everyone

![Network Types by Size](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Internet_map_1024_-_transparent%2C_inverted.png/640px-Internet_map_1024_-_transparent%2C_inverted.png)

### Types of Networks by Who Controls Them

#### Client-Server Networks
- Has powerful central computers (servers) that provide services
- Other computers (clients) ask the servers for what they need
- Examples: 
  - Email systems (your computer asks the mail server for new messages)
  - Websites (your browser asks the web server for pages)
  - School networks (students' computers connect to school servers)

![Client-Server Network](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Client-server-model.svg/500px-Client-server-model.svg.png)

#### Peer-to-Peer Networks
- All computers are equal - no main server
- Each computer can both give and receive services
- Examples:
  - File sharing networks
  - Some video calling services
  - Small home networks

![Peer-to-Peer Network](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3f/P2P-network.svg/500px-P2P-network.svg.png)

### Types of Networks by Connection

#### Wired Networks
- Uses physical cables to connect devices
- Common types:
  - Ethernet cables (the most common type in offices and homes)
  - Fiber optic cables (super fast using light signals)
  - Coaxial cables (used for cable TV and some internet)

#### Wireless Networks
- No cables needed - uses radio waves
- Examples:
  - Wi-Fi (wireless internet in homes and businesses)
  - Bluetooth (short-range connections)
  - Cellular networks (for mobile phones)

## How Networks Are Built

### The Network Layers
Networks are built in layers, like a cake. Each layer does a specific job and works with the layers above and below it. This makes networks easier to build and fix.

The most famous model is called the OSI model (Open Systems Interconnection). It has 7 layers:

1. **Physical Layer** - The actual cables and signals
2. **Data Link Layer** - Getting data between directly connected devices
3. **Network Layer** - Finding paths across multiple networks
4. **Transport Layer** - Making sure data arrives correctly
5. **Session Layer** - Setting up and managing connections
6. **Presentation Layer** - Formatting and encrypting data
7. **Application Layer** - Programs that users interact with

![OSI Model](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/800px-OSI_Model_v1.svg.png)

In real life, we often use a simpler model called the TCP/IP model, which has just 4 or 5 layers:

1. **Network Access/Physical Layer** - Combines OSI's Physical and Data Link
2. **Internet Layer** - Same as OSI's Network Layer
3. **Transport Layer** - Same as OSI's Transport Layer
4. **Application Layer** - Combines OSI's Session, Presentation, and Application

![TCP/IP Model](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/UDP_encapsulation.svg/350px-UDP_encapsulation.svg.png)

### How Data Travels Through Networks

When you send data (like an email), it travels down through all the layers on your computer, across the network, and up through all the layers on the receiving computer:

1. Your email is broken into small pieces called packets
2. Each layer adds its own information (called headers)
3. The packets travel across the network
4. The receiving computer removes the headers as the data moves up through its layers
5. The email is reassembled and delivered

This is like sending a letter:
- You write the letter (Application Layer)
- Put it in an envelope with an address (Transport Layer)
- The post office figures out how to route it (Network Layer)
- Mail carriers deliver it locally (Data Link Layer)
- It physically travels there (Physical Layer)

## The Physical Layer

The Physical Layer is the foundation of networking. It deals with the actual physical connections and the electrical, optical, or radio signals that carry data.

### What It Does
- Transmits raw bits (1s and 0s) from one device to another
- Defines physical characteristics like cables, pins, voltages
- Handles the conversion between digital data and signals

### Types of Transmission Media

#### Wired Media
1. **Twisted Pair Cable**
   - Most common in LANs
   - Contains pairs of insulated copper wires twisted together
   - Two types:
      - Unshielded Twisted Pair (UTP) - Common in homes and offices
      - Shielded Twisted Pair (STP) - Better protection against interference
   - Categories: Cat5, Cat5e, Cat6, Cat7 (higher number = better performance)

![Twisted Pair Cable](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/UTP_cable.jpg/640px-UTP_cable.jpg)

2. **Coaxial Cable**
   - Has a central copper core surrounded by insulation and shielding
   - Used for cable TV and some internet connections
   - Better against interference than twisted pair
   - More expensive and less flexible

![Coaxial Cable](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f4/Coaxial_cable_cutaway.svg/640px-Coaxial_cable_cutaway.svg.png)

3. **Fiber Optic Cable**
   - Uses glass/plastic fibers to transmit light signals
   - Much faster than copper cables
   - Immune to electrical interference
   - Can transmit over very long distances
   - More expensive and harder to install

![Fiber Optic Cable](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0c/Optical_fiber_cable.jpg/640px-Optical_fiber_cable.jpg)

#### Wireless Media
1. **Radio Waves**
   - Used in Wi-Fi, Bluetooth, and cellular networks
   - Can pass through walls but weaken with distance
   - Subject to interference from other devices

2. **Microwaves**
   - Higher frequency than radio waves
   - Used for line-of-sight transmission
   - Examples: Some wireless networks and satellite communication

3. **Infrared**
   - Short-range, line-of-sight transmission
   - Used in TV remotes and some older devices
   - Cannot pass through walls

### Network Devices at the Physical Layer

#### Repeaters
- Boost signals to extend the distance they can travel
- Just regenerate the signal, don't understand the data

#### Hubs
- Connect multiple devices in a network
- When a hub receives data, it sends it to all connected devices
- Simple and cheap but inefficient (creates lots of unnecessary traffic)

![Hub](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Network_hub.jpg/640px-Network_hub.jpg)

#### Network Interface Cards (NICs)
- Connect a computer to a network
- Every networked device has a NIC (built-in or added)
- Has a unique MAC address (like a device fingerprint)

![Network Interface Card](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Network_card.jpg/640px-Network_card.jpg)

## The Data Link Layer

The Data Link Layer is responsible for moving data across a single link between two devices. It deals with local delivery of data and handles errors that might occur at the Physical Layer.

### What It Does
- Places data into frames (like putting a letter in an envelope)
- Manages access to the physical medium (who can talk when)
- Detects and sometimes corrects errors
- Controls flow of data

### MAC Addresses
- MAC (Media Access Control) addresses are physical addresses
- Every network interface has a unique MAC address
- 48 bits (6 bytes) long, usually written as 12 hexadecimal digits
- Example: `00:1A:2B:3C:4D:5E`
- First half identifies the manufacturer, second half is the serial number
- Unlike IP addresses, MAC addresses are permanent and don't change based on location

![MAC Address](https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/MAC-48_Address.svg/640px-MAC-48_Address.svg.png)

### Framing
The Data Link Layer packages data into frames that include:
- Header with source and destination MAC addresses
- Payload (the actual data)
- Trailer with error checking information

![Data Link Frame](https://upload.wikimedia.org/wikipedia/commons/thumb/4/42/Data_Link_Frame.png/640px-Data_Link_Frame.png)

### Error Detection and Correction
Two common methods:
1. **Parity Check**
   - Adds a parity bit to detect single-bit errors
   - Simple but not very powerful

2. **Cyclic Redundancy Check (CRC)**
   - More powerful error detection
   - Uses polynomial division to create a checksum
   - Can detect multiple-bit errors

### Media Access Control Methods
These determine how devices share the physical medium:

1. **CSMA/CD (Carrier Sense Multiple Access with Collision Detection)**
   - Used in traditional Ethernet
   - Devices listen before transmitting
   - If a collision occurs, stop, wait a random time, and try again
   - Like a conversation where everyone stops if two people speak at once

2. **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)**
   - Used in Wi-Fi
   - Tries to avoid collisions in the first place
   - Devices announce their intention to transmit

3. **Token Passing**
   - Used in Token Ring networks
   - A special message (token) is passed around
   - Only the device with the token can transmit
   - Like passing a talking stick in a meeting

### Network Devices at the Data Link Layer

#### Bridges
- Connect two network segments
- Can filter traffic based on MAC addresses
- Smarter than repeaters but simpler than routers

#### Switches
- Modern replacement for hubs
- Direct data only to the intended recipient
- Maintain a MAC address table to know which device is on which port
- Much more efficient than hubs

![Network Switch](https://upload.wikimedia.org/wikipedia/commons/thumb/3/37/Cisco_Catalyst_3750_Switch.jpg/640px-Cisco_Catalyst_3750_Switch.jpg)

### Ethernet
The most common Data Link Layer protocol:
- Developed in the 1970s and continually improved
- Uses CSMA/CD for media access
- Speeds range from 10 Mbps to 400 Gbps
- Dominates wired local area networking

### Other Data Link Layer Protocols
1. **Point-to-Point Protocol (PPP)**
   - Used for direct connections between two devices
   - Common in dial-up and some broadband connections

2. **Wi-Fi (IEEE 802.11)**
   - The wireless standard for local networks
   - Multiple versions (a, b, g, n, ac, ax) with increasing speeds
   - Uses CSMA/CA to avoid collisions

3. **HDLC (High-level Data Link Control)**
   - Used in some WAN connections
   - Based on older SDLC protocol

## The Network Layer

The Network Layer handles routing data across multiple networks to get from the source to the final destination. It's like the postal system figuring out which route a package should take.

### What It Does
- Finds the best path across multiple networks
- Handles logical addressing (IP addresses)
- Breaks large messages into smaller packets if needed
- Reassembles packets at the destination

### IP Addresses
- Logical addresses assigned to devices on a network
- Two main versions:
  - IPv4: 32-bit addresses (e.g., 192.168.1.1)
  - IPv6: 128-bit addresses (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334)
- Unlike MAC addresses, IP addresses can change when a device moves to a different network

![IP Address Structure](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Ipv4_address.svg/640px-Ipv4_address.svg.png)

### IPv4 Addressing
- 32-bit addresses divided into four 8-bit numbers (0-255)
- Example: 192.168.1.1
- Has five classes (A, B, C, D, E) for different network sizes
- About 4.3 billion possible addresses (almost all used up now)
- Special addresses:
  - 127.0.0.1: Loopback (your own computer)
  - 192.168.x.x, 10.x.x.x: Private addresses (for internal networks)

### IPv6 Addressing
- Created to solve IPv4 address shortage
- 128-bit addresses written as eight groups of four hexadecimal digits
- Example: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
- Can be shortened by removing leading zeros and replacing consecutive zero groups with ::
- Above example shortened: 2001:db8:85a3::8a2e:370:7334
- About 340 undecillion (3.4×10^38) possible addresses

### Subnetting
- Dividing a large network into smaller subnetworks
- Makes network management easier
- Uses a subnet mask to define which part is the network and which part identifies the host
- Example: 192.168.1.0/24 means the first 24 bits identify the network

![Subnetting](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b3/Subnetting_Concept.svg/640px-Subnetting_Concept.svg.png)

### Routing
- The process of finding the best path from source to destination
- Handled by routers, which maintain routing tables
- Routing can be:
  - Static: Manually configured by administrators
  - Dynamic: Automatically updated using routing protocols

### Routing Protocols
1. **RIP (Routing Information Protocol)**
   - Simple but limited
   - Measures distance in hops (number of routers)
   - Limited to 15 hops

2. **OSPF (Open Shortest Path First)**
   - More sophisticated than RIP
   - Uses "cost" based on bandwidth
   - Better for large networks

3. **BGP (Border Gateway Protocol)**
   - Used for routing between different organizations
   - The main routing protocol of the internet
   - Very complex but very flexible

### Network Devices at the Network Layer

#### Routers
- Connect different networks together
- Make decisions based on IP addresses
- Maintain routing tables to determine the best path
- Can connect different types of networks (like Ethernet to Wi-Fi)

![Router](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Cisco_2600_Series_Router_rear_view.jpg/640px-Cisco_2600_Series_Router_rear_view.jpg)

### Other Network Layer Functions

#### Network Address Translation (NAT)
- Allows multiple devices to share one public IP address
- Important due to shortage of IPv4 addresses
- Commonly used in home routers

![NAT](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/NAT_Concept-en.svg/640px-NAT_Concept-en.svg.png)

#### ICMP (Internet Control Message Protocol)
- Used for error reporting and diagnostics
- The protocol behind the "ping" command
- Also used for "traceroute" to see the path packets take

## The Transport Layer

The Transport Layer creates a connection between the source and destination applications, ensuring data arrives correctly and in order.

### What It Does
- Creates end-to-end connections between applications
- Breaks data into segments
- Can ensure reliable delivery and correct order
- Handles flow control (not sending data too fast)
- Provides error recovery
- Identifies which application should receive the data using port numbers

### Port Numbers
- 16-bit numbers (0-65535) identifying specific applications
- Combined with IP addresses to create a complete address (socket)
- Well-known ports (0-1023) are reserved for common services:
  - 80: HTTP (web)
  - 443: HTTPS (secure web)
  - 25: SMTP (email sending)
  - 110: POP3 (email receiving)
  - 21: FTP (file transfer)
  - 22: SSH (secure shell)
  - 53: DNS (domain name system)

### Main Transport Protocols

#### TCP (Transmission Control Protocol)
- Connection-oriented (establishes a connection before sending data)
- Reliable delivery (acknowledges received data)
- Ensures data arrives in the correct order
- Flow control prevents overwhelming the receiver
- Slower but more reliable
- Used when accuracy is critical (web browsing, file transfers, email)

![TCP Handshake](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/Tcp_state_diagram_fixed_new.svg/640px-Tcp_state_diagram_fixed_new.svg.png)

#### UDP (User Datagram Protocol)
- Connectionless (no connection established)
- No guarantee of delivery or ordering
- No flow control
- Faster but less reliable
- Used when speed is more important than perfect delivery (video streaming, online gaming, DNS lookups)

### TCP Three-Way Handshake
How TCP establishes a connection:
1. Client sends SYN (synchronize) packet
2. Server responds with SYN-ACK (synchronize-acknowledge)
3. Client sends ACK (acknowledge)
4. Connection established

![TCP Three-Way Handshake](https://upload.wikimedia.org/wikipedia/commons/thumb/5/55/TCP_CLOSE.svg/640px-TCP_CLOSE.svg.png)

### Flow Control
- Prevents the sender from overwhelming the receiver
- The receiver tells the sender how much data it can accept (window size)
- If the window size is 0, the sender waits

### Congestion Control
- Prevents too much traffic on the network
- TCP slows down when it detects congestion
- Uses various algorithms to detect and respond to congestion

### Error Detection and Recovery
- Transport layer can detect corrupted data
- TCP can request retransmission of lost or corrupted segments
- Uses checksums and acknowledgments

## The Application Layer

The Application Layer is the top layer that users interact with directly. It provides network services to applications and handles the details of particular applications.

### What It Does
- Provides interfaces for applications to use network services
- Implements common application protocols
- Handles user authentication when needed
- Determines resource availability
- Synchronizes communication

### Common Application Layer Protocols

#### HTTP (Hypertext Transfer Protocol)
- Used for web browsing
- How web browsers request and receive web pages
- Default port: 80
- HTTPS is the secure version (port 443)
- Based on a request-response model

![HTTP Request-Response](https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Internet-client-server.svg/640px-Internet-client-server.svg.png)

#### SMTP (Simple Mail Transfer Protocol)
- Used for sending email
- Default port: 25
- Works with other protocols like POP3 or IMAP for receiving email

#### FTP (File Transfer Protocol)
- Used for uploading and downloading files
- Default port: 21 (control) and 20 (data)
- Supports authentication
- Has both text and binary transfer modes

#### DNS (Domain Name System)
- Translates domain names to IP addresses
- Default port: 53
- Hierarchical, distributed database
- Without DNS, you'd need to remember IP addresses instead of names

![DNS Lookup](https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/DNS_queue.svg/640px-DNS_queue.svg.png)

#### DHCP (Dynamic Host Configuration Protocol)
- Automatically assigns IP addresses to devices
- Also provides subnet mask, default gateway, and DNS server information
- Makes network administration much easier

#### SSH (Secure Shell)
- For secure remote login and command execution
- Default port: 22
- Encrypted alternative to older protocols like Telnet

#### SNMP (Simple Network Management Protocol)
- Used for network management and monitoring
- Allows collecting information from network devices
- Can also be used to configure devices remotely

### Domain Name System (DNS) in Detail
- Works like a phone book for the internet
- Converts human-friendly names (www.example.com) to IP addresses (93.184.216.34)
- Hierarchical structure:
  - Root domain (.)
  - Top-level domains (.com, .org, .edu)
  - Second-level domains (example.com)
  - Subdomains (www.example.com)
- Uses a distributed database to spread the load
- Caching improves performance

### Web Technologies
- **HTML**: Language for creating web pages
- **CSS**: For styling web pages
- **JavaScript**: Adds interactivity to web pages
- **AJAX**: Allows updating parts of a web page without reloading
- **REST APIs**: How many web services communicate

## Keeping Networks Safe

### Network Security Threats
1. **Malware**:
   - Viruses: Need a host program to spread
   - Worms: Self-replicating, no host needed
   - Trojans: Disguised as legitimate software
   - Ransomware: Encrypts data and demands payment

2. **Social Engineering**:
   - Phishing: Fake emails/websites to steal information
   - Pretexting: Creating a fake scenario to get information
   - Baiting: Offering something desirable to trick users

3. **Denial of Service (DoS)**:
   - Floods a system with traffic to make it unavailable
   - Distributed DoS (DDoS) uses multiple attacking computers

4. **Man-in-the-Middle Attacks**:
   - Attacker secretly relays/alters communication
   - Like someone reading your mail before delivery

### Security Measures

#### Firewalls
- Act as gatekeepers for network traffic
- Can be hardware devices or software
- Use rules to determine what traffic is allowed
- Types:
  - Packet filtering: Examines individual packets
  - Stateful inspection: Tracks active connections
  - Application-level: Understands specific protocols
  - Next-generation: Combines multiple security features

![Firewall](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Firewall.png/640px-Firewall.png)

#### Encryption
- Scrambles data so only authorized parties can read it
- Two main types:
  - Symmetric: Same key to encrypt and decrypt
  - Asymmetric: Public key to encrypt, private key to decrypt
- Used in HTTPS, VPNs, wireless security

![Encryption](https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Symmetric_key_encryption.svg/640px-Symmetric_key_encryption.svg.png)

#### Virtual Private Networks (VPNs)
- Create secure "tunnels" through public networks
- Encrypt all traffic between points
- Allow secure access to private networks from outside
- Mask your real IP address and location

![VPN](https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/VPN_overview-en.svg/640px-VPN_overview-en.svg.png)

#### Intrusion Detection/Prevention Systems
- IDS: Monitors network for suspicious activity
- IPS: Actively blocks suspicious activity
- Can detect attacks firewalls might miss

#### Authentication and Authorization
- Authentication: Verifying who you are (passwords, biometrics)
- Authorization: Determining what you can access
- Multi-factor authentication adds security (something you know + something you have)

### Wireless Security
- **WEP**: Old and insecure
- **WPA**: Better but still vulnerable
- **WPA2/WPA3**: Current standards for Wi-Fi security
- Other tips:
  - Change default router passwords
  - Hide SSID (network name)
  - Use MAC address filtering
  - Keep firmware updated

## Wireless Networks

### How Wireless Networks Work
- Use radio waves instead of cables
- Data converted to radio signals and back
- Different frequencies for different types of networks

### Types of Wireless Networks

#### Wi-Fi (IEEE 802.11)
- The standard for wireless LANs
- Different versions (a, b, g, n, ac, ax) with increasing speeds
- Typical range: up to 100 meters (outdoors)
- Common in homes, offices, public hotspots

![Wi-Fi Network](https://upload.wikimedia.org/wikipedia/commons/thumb/f/fc/Wi-Fi_Logo.svg/640px-Wi-Fi_Logo.svg.png)

#### Bluetooth
- Short-range wireless (about 10 meters)
- Low power consumption
- Used for peripherals, headsets, IoT devices
- Different versions with increasing speeds and range

#### Cellular Networks
- Wide-area wireless networks
- Operated by telecommunications companies
- Generations:
  - 1G: Analog voice
  - 2G: Digital voice and text
  - 3G: Mobile internet
  - 4G: Fast mobile internet
  - 5G: Ultra-fast speeds, low latency, more connections

![Cellular Network](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Frequency_reuse.svg/640px-Frequency_reuse.svg.png)

#### Satellite
- Global coverage including remote areas
- Higher latency (delay) than other methods
- More affected by weather
- Used where other options aren't available

### Wireless Network Components

#### Access Points
- Connect wireless devices to a wired network
- Broadcast network name (SSID)
- Handle security and authentication
- Modern routers usually include access points

#### Wireless Controllers
- Manage multiple access points centrally
- Used in larger networks (businesses, campuses)
- Handle roaming, load balancing, security

### Wireless Network Issues

#### Interference
- Other devices using same frequency
- Physical obstacles (walls, floors)
- Solutions:
  - Change channels
  - Use 5 GHz instead of 2.4 GHz
  - Add access points

#### Security Concerns
- Easier to intercept than wired networks
- Unauthorized access more common
- Solutions:
  - Strong encryption (WPA2/WPA3)
  - Strong passwords
  - Network segregation (guest networks)

## New Network Technologies

### Cloud Computing
- Delivering computing services over the internet
- Types:
  - SaaS (Software as a Service): Applications like Gmail
  - PaaS (Platform as a Service): Development platforms
  - IaaS (Infrastructure as a Service): Virtual servers and storage
- Benefits: Scalability, lower costs, accessibility

![Cloud Computing](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/Cloud_computing.svg/640px-Cloud_computing.svg.png)

### Internet of Things (IoT)
- Everyday objects connected to the internet
- Examples: Smart thermostats, connected appliances, wearables
- Creates vast networks of devices
- Challenges: Security, privacy, standardization

![Internet of Things](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/Internet_of_Things.jpg/640px-Internet_of_Things.jpg)

### Software-Defined Networking (SDN)
- Separates network control from data forwarding
- Makes networks programmable
- More flexible and easier to manage
- Centralized control with global view of network

### 5G Networks
- Fifth generation of cellular networks
- Much faster than 4G (up to 10 Gbps)
- Very low latency (1 millisecond or less)
- Can connect many more devices
- Enables new applications (autonomous vehicles, smart cities)

### Edge Computing
- Processing data near where it's created, not in central cloud
- Reduces latency and bandwidth use
- Important for time-sensitive applications
- Complements cloud computing

![Edge Computing](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Edge_computing_infrastructure.png/640px-Edge_computing_infrastructure.png)

### Network Function Virtualization (NFV)
- Replaces hardware network appliances with software
- Runs network functions on standard servers
- More flexible and cost-effective
- Easier to scale up or down

### Blockchain Networks
- Distributed ledger technology
- No central authority needed
- Secure and transparent
- Used for cryptocurrencies and beyond

## Summary of Key Concepts

### The Network Layers Work Together
- **Physical Layer**: The actual cables and signals
- **Data Link Layer**: Moves data between directly connected devices
- **Network Layer**: Finds paths across multiple networks
- **Transport Layer**: Ensures data arrives correctly at the right application
- **Application Layer**: Provides services to software applications

### Common Network Devices
- **Repeaters and Hubs**: Extend networks (Physical Layer)
- **Bridges and Switches**: Connect network segments intelligently (Data Link Layer)
- **Routers**: Connect different networks (Network Layer)
- **Firewalls**: Protect networks (Multiple layers)
- **Load Balancers**: Distribute traffic among servers (Transport/Application Layers)

### Design Principles to Remember
1. **Layering**: Each layer has a specific job
2. **Encapsulation**: Each layer adds its own headers/trailers
3. **Addressing**: Different addresses for different purposes (MAC, IP, ports)
4. **Routing**: Finding the best path through networks
5. **Error Control**: Detecting and fixing problems
6. **Flow Control**: Not sending data too fast
7. **Security**: Protecting data and resources