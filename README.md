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


# Network Sharing Methods

## Two Ways to Share Switched Networks

### 1. Circuit Switching
- **Definition:** End-to-end resources are allocated and reserved for a flow from source to destination. The process involves:
  - The source sends a request to the destination.
  - Switches create circuits after performing admission control.

- **Techniques:**
  - **Time Division Multiplexing (TDM):** Time is divided into slots, and data is sent only during its allocated slot.
  - **Frequency Division Multiplexing (FDM):** Optical or electromagnetic frequencies are divided into bands, and data is sent within a specific narrow band.

- **Phases of Circuit Switching:**
  1. **Circuit Establishment**
  2. **Data Transfer**
  3. **Circuit Teardown**

### 2. Packet Switching
- **Definition:** Data is broken down into smaller chunks called packets. Each packet contains destination information and is treated independently.

- **Advantages:**
  - Simpler to implement.
  - Efficient use of network resources.

- **Disadvantages:**
  - Requires buffer management.
  - Needs congestion control.

---

# Network Performance Metrics

## Key Metrics:
1. **Delay (Latency):** How long it takes for a packet to travel from source to destination.
2. **Loss:** The fraction of packets sent by the source that fail to reach the destination.
3. **Throughput:** The rate at which data is received by the destination.

---

## Delay Components:
1. **Transmission Delay:**  
   Time taken to push all bits of a packet onto the link.  
   **Formula:**  
   ```
   Packet Transmission Delay = L (bits) / R (bits/sec)
   ```
   Where:  
   - `L` is the packet size.  
   - `R` is the link bandwidth.  
     Bandwidth refers to the maximum rate at which data can be transmitted over a network link in a given amount of time.

2. **Propagation Delay:**  
   How long it takes to move one bit from one end of the link to the other.  
   **Formula:**  
   ```
   Propagation Delay = d (meters) / s (meters/sec)
   ```
   Where:  
   - `d` is the link length (distance).  
   - `s` is the propagation speed of the signal in the link medium.  

   **Pipe View:** Transmission delay decreases as the bandwidth increases.

3. **Queueing Delay:**  
   How long a packet has to sit in a buffer before it is processed.  
   - Queueing delay can vary significantly for the same router at different times (based on load).  
   - Typically measured in microseconds (µs) or milliseconds (ms).  

   **Transient Overload:**  
   Refers to a temporary condition where the arrival rate of packets exceeds the service rate of the network device (e.g., a router or switch). This causes packets to queue up, leading to increased delays or even packet drops if the buffer becomes full.  

   **Formula:**  
   ```
   Queueing Delay = Number of Packets * Transmission Delay
   ```

   ![Queueing Delay](problem3.png)

4. **Processing Delay:**  
   Time taken by the switch to process a packet.  
   - When a packet arrives at a packet switch, the switch needs to perform some actions before putting it onto the output link.

---

## Nodal Delay:
The total time for a packet to reach the other end of the link.  
**Formula:**  
```
d_nodal = d_proc + d_queue + d_trans + d_prop
```

For the total delay across multiple nodes:  
```
d_end_to_end = N * d_nodal
```

---

## Loss:
- What fraction of packets sent to the destination are dropped?

---

## Throughput:
- At what rate (bits/time unit) is the destination receiving data from the source?  
- **Formula:**  
  ```
  Throughput = F / T (bits/sec)
  ```
  Where:  
  - `F` is the file size in bits.  
  - `T` is the time in seconds.  

  Throughput is always referred to on the destination side and is also known as **goodput**.

---

## Goals:
- **Low latency**
- **Low loss rate**
- **High throughput**

---

## Visual References:
- **Circuit and Packet Switching Problem:**  
  ![Circuit and Packet Switching Problem](problem1.png)
- **Transmission Delay:**  
  ![Transmission Delay](problem2.png)
- **Prefix Refresher:**  
  ![Prefix Refresher](prefix_refresher.png)

# Layered Internet Protocol Stack

## Overview of Layers
1. **Application Layer**: Supports network applications (e.g., HTTP, DNS, SMTP).
2. **Transport Layer**: Handles process-to-process data transfer (e.g., TCP, UDP).
3. **Network Layer**: Manages routing of datagrams from source to destination (e.g., IP, routing protocols).
4. **Link Layer**: Transfers data between neighboring network elements (e.g., Ethernet, WiFi).
5. **Physical Layer**: Transmits raw bits "on the wire."

---

## Key Concepts

### Data Exchange Across Layers
1. **Application Layer**: Exchanges messages to implement application services using the transport layer.
2. **Transport Layer**:
   - Transfers messages `M` from one process to another using the services of the network layer.
   - Encapsulates the application layer message `M` with a transport layer header `Ht` to create a transport layer segment.
3. **Network Layer**:
   - Encapsulates the transport-layer segment `[Ht | M]` with a network-layer header `Hn` to create a network-layer datagram.
   - Transfers the transport-layer segment `[Ht | M]` from one host to another using link-layer services.
4. **Link Layer**:
   - Transfers datagrams `[Hn | Ht | M]` from one host to a neighboring host.
   - Encapsulates the network-layer datagram `[Hn | Ht | M]` with a link-layer header `Hl` to create a link-layer frame.

---

## Network Application
A **network application** is composed of two or more processes running in end systems that exchange messages over a network to achieve a specific goal.

- Programs use the **socket API** to send messages.

---

## Socket
A **socket** is the interface between the application layer and the transport layer.

### Specifying Data Destination:
1. **Service**: Transport layer protocol (e.g., TCP or UDP).
2. **IP Address**: A 32-bit address uniquely identifying the host.
3. **Port**: A number (0–65535) identifying the socket.

**Analogy**:  
- **IP Address** = Building Address.  
- **Port** = Office Number.

---

## Transport Services

### 1. **UDP (User Datagram Protocol)**
- Best-effort, unreliable data transfer.
- Allows sending as much data as needed (e.g., live streaming).
- No recovery of lost packets.

### 2. **TCP (Transmission Control Protocol)**
- Connection-oriented, reliable, and in-order data transfer.
- Guarantees sent data is received.
- Includes **congestion control** to throttle sending when the network is overloaded.

**Congestion Control**:  
Manages and regulates network traffic to prevent congestion. Congestion occurs when demand exceeds network capacity, leading to packet loss, delays, and reduced performance.

---

## Network Application Architectures

### 1. **Client-Server Architecture**
- A **server** process handles requests from **clients** (users).

### 2. **Peer-to-Peer (P2P) Architecture**
- No dedicated servers.
- **Peers** communicate directly with each other.

# World Wide Web (WWW)

## Overview
- The WWW is a distributed database of components and resources linked through HTTP (Hypertext Transfer Protocol).

## Web Pages
- Web pages consist of objects.
- A typical web page includes a base HTML file and several referenced objects.
- Each object is identified by a URL (Uniform Resource Locator).

**URL Format**:  
`protocol://host-name[:port]/directory-path/resource`  
**Example**:  
`http://www.example.com/some-example-path/image.png`

---

## Accessing Web Pages
- **Client-Server Architecture** with TCP transport.
- Web browsers (clients) request web pages from web servers.
- HTTP defines the communication protocol between web browsers and servers.

### HTTP Communication Steps
1. User enters URL: `http://www.example.com/some-example-path/image.png`
2. Client initiates a TCP connection to the server at `www.example.com` on port 80.
3. Server listening on port 80 accepts the connection.
4. Client sends an HTTP request for the object (`some-example-path/image.png`) over the TCP connection.
5. Server responds with an HTTP response message containing the requested object.

---

## HTTP Request Message Format
- **Request Line**: Specifies the method, resource, and protocol version.  
  Example: `GET /somedir/page.html HTTP/1.1`
- **Header Lines**: Provide information or modify the request.  
  Example:  
  ```
  HOST: www.example.com  
  User-agent: Mozilla/4.0  
  Connection: close  
  Accept-language: fr
  ```
- **Body**: Optional data (e.g., for "POST" requests).

### Method Types
1. **GET, HEAD**  
   - Retrieve information.  
   - `HEAD` is like `GET` but excludes the object.  
   - User data can be included in the URL.  
     Example: `http://www.example.com/animalsearch?monkeys&banana`

2. **POST**  
   - Sends data to the server (e.g., web forms).

3. **PUT**  
   - Uploads a file in the request's entity body to the specified path in the URL.

4. **DELETE**  
   - Deletes the file specified in the URL.

---

## Difference Between PUT and POST
- **PUT**:  
  - Used to update or create a resource.  
  - Idempotent: Making the same PUT request multiple times will produce the same result.

- **POST**:  
  - Used to send data to a server to create a new resource.  
  - Not idempotent: Repeating the same POST request may result in multiple resources being created.

---

## HTTP Response Message Format
- **Status Line**: Protocol version, status code, status phrase.  
  Example: `HTTP/1.1 200 OK`
- **Response Headers**: Provide additional information.
- **Body**: Contains optional data (e.g., requested object).

### Common HTTP Status Codes
- **200 OK**: Request succeeded; the requested object is in the response.
- **301 Moved Permanently**: Object moved; the new location is provided.
- **400 Bad Request**: Request not understood by the server.
- **404 Not Found**: Requested document not found on the server.
- **505 HTTP Version Not Supported**: Server does not support the HTTP protocol version used.

---

## HTTP Characteristics
- **Stateless Protocol**:  
  - Servers do not retain state information.  
  - **Pros**: Improves scalability on the server side.  
  - **Cons**: Persistent state is needed for some applications.

### Retaining State: Cookies
- **Client-Side State Maintenance**:  
  - Client stores small pieces of state for the server.  
  - Sends state data in future requests.  
- **Uses of Cookies**:  
  - Authorization.  
  - Shopping carts.  
  - User session state (e.g., web emails).

---

## HTTP Performance
- **RTT (Round Trip Time)**: Time for a packet to travel from client to server and back.  
- **HTTP Response Time (Per Object)**:  
  - 1 RTT to initiate a TCP connection.  
  - 1 RTT for HTTP request and first bytes of HTTP response.  
  - File transmission time.  
  **Formula**:  
  `HTTP Response Time = 2 * RTT + File Transmission Time`

### Connection Types
1. **Non-Persistent HTTP**  
   - Separate TCP connection for each object.  
   - **Optimization**: Use parallel connections to reduce response time.

2. **Persistent HTTP**  
   - Maintains TCP connection across multiple requests.  

### Response Times for Retrieving `n` Small Objects
| Connection Type              | Response Time                  |
|------------------------------|---------------------------------|
| Non-Persistent Serial        | `2 * RTT * n`                 |
| Non-Persistent (m Parallel)  | `2 * RTT * (n/m)`             |
| Persistent Non-Pipelined     | `(1 + n) * RTT`               |
| Persistent Pipelined         | `2 * RTT` (for first requests) |
