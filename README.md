# Application of Networks

## Networks
- Networks consist of **links** that connect **nodes** and can carry information between them.  
- **Nodes** connected in the network are called **hosts** or **end systems**.

## Internet
- Nodes are connected by **packet switches** and **communication links**.  
- Computers connected to a network that participate directly in communication are classified as **hosts**.  
- Devices that users commonly interact with are called **end devices**.  
- **Packet Switching** is a method of transferring data in the form of packets over a network.  
- End systems connect to the Internet through **Internet Service Providers (ISP)**, which are organized in a hierarchy.  
- Information is packaged into chunks of data called **packets**, which traverse a route of links and switches to reach their destination.  
- **Transmission rates** (bandwidth) are measured in bits/sec.

## Applications and Network Layers
- Applications view the Internet as a **black-box infrastructure** providing specific services.  
- Applications access these services through **well-defined interfaces**.  
- Computer networks separate responsibilities into **layers**, where each layer provides services to the one above it.

---

## Protocol
- A protocol is like a **blueprint** that specifies a common format for communication exchange.  
- **In computer networks**, protocols define:  
  - The **format** and **order** of messages sent and received.  
  - Actions taken upon message transmission, receipt, or other events.

---

## Network Edge
- The **network edge** is the point where devices (end-user systems, IoT devices, servers) connect to the network infrastructure.  
- Servers are often housed in **data centers**.

## Physical Medium
- Communication occurs by propagating electromagnetic waves or optical pulses across a physical medium.  
- **Physical media** can be:  
  - **Guided media**: Twisted-pair copper wire, coaxial cable.  
  - **Unguided media**: Wireless LAN, digital satellite channels.

---

## Data Transmission
- Long messages from a source system are broken into smaller **packets** for transmission.  
- Packets travel through **communication links** and **packet switches** from source to destination.  
- **Transmission time for a packet**:  
  ```
  Time = L / R (where L = packet size in bits, R = transmission rate in bits/sec)
  ```

## Store-and-Forward Transmission
- Most packet switches use **store-and-forward transmission**:  
  - The switch must **receive the entire packet** before transmitting the first bit to the outbound link.  
- **End-to-end delay for one packet** across N links:  
  ```
  Delay = N * (L / R)
  ```

---

## Packet Switches
- Each packet switch has multiple links attached, and for each link, an **output buffer (queue)** stores packets waiting for transmission.  

### Packet Loss
- If a packet arrives at a busy link, it waits in the **output buffer** (queueing delay).  
- If the buffer is full, **packet loss** occurs, and either the arriving packet or a queued packet is dropped.

### Packet Forwarding
- The router receives a packet from one link and **forwards** it to another attached communication link.
