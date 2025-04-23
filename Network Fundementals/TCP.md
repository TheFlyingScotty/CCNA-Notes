Related: [[Network Fundamentals]]

TCP (Transmission Control Protocol) is a connection-oriented protocol that operates at the Transport Layer (Layer 4) of the OSI model. It is designed to provide reliable communication between devices over a network by ensuring that data is delivered accurately and in the correct order.

### Key Features of TCP:

1. **Connection-Oriented Communication**:
    
    - TCP establishes a connection between the sender and receiver before data transfer begins. This is done using a three-way handshake process:
        - **SYN**: The sender sends a synchronization (SYN) packet to initiate the connection.
        - **SYN-ACK**: The receiver acknowledges the SYN and sends its own SYN packet.
        - **ACK**: The sender acknowledges the receiver's SYN, completing the handshake.
2. **Reliable Data Transfer**:
    
    - TCP ensures that all data is delivered without errors. If a packet is lost or corrupted during transmission, TCP retransmits it.
3. **Error Checking**:
    
    - TCP uses checksums to detect errors in transmitted data. If an error is detected, the affected packet is retransmitted.
4. **Ordered Delivery**:
    
    - TCP assigns sequence numbers to packets, ensuring that data is reassembled in the correct order at the receiver, even if packets arrive out of sequence.
5. **Flow Control**:
    
    - TCP uses flow control mechanisms, such as the sliding window protocol, to prevent the sender from overwhelming the receiver with too much data at once.
6. **Congestion Control**:
    
    - TCP monitors network conditions and adjusts the rate of data transmission to avoid congestion and packet loss.
7. **Full-Duplex Communication**:
    
    - TCP allows simultaneous two-way communication between the sender and receiver.
8. **Port Numbers**:
    
    - TCP uses port numbers to identify specific applications or services on a device, enabling multiple applications to use the network simultaneously.

### How TCP Works:

1. **Connection Establishment**:
    
    - The three-way handshake establishes a reliable connection between the sender and receiver.
2. **Data Transmission**:
    
    - Data is divided into segments, each with a sequence number. TCP ensures that all segments are delivered and reassembled in the correct order.
3. **Acknowledgments**:
    
    - The receiver sends acknowledgments (ACKs) to confirm the successful receipt of data. If an acknowledgment is not received, TCP retransmits the missing data.
4. **Connection Termination**:
    
    - The connection is closed using a four-step process:
        - The sender sends a FIN (finish) packet.
        - The receiver acknowledges the FIN with an ACK.
        - The receiver sends its own FIN packet.
        - The sender acknowledges the receiver's FIN, completing the termination.

### Advantages of TCP:

- Reliable and error-free communication.
- Ensures data is delivered in the correct order.
- Handles congestion and flow control effectively.

### Disadvantages of TCP:

- Higher overhead due to connection setup, acknowledgments, and retransmissions.
- Slower compared to connectionless protocols like [[UDP]].

### Common Applications of TCP:

- Web browsing (HTTP/HTTPS).
- Email (SMTP, IMAP, POP3).
- File transfers (FTP).
- Remote access (SSH, Telnet).

In summary, TCP is a robust and reliable protocol that ensures accurate and ordered data delivery, making it ideal for applications where reliability is critical. However, its overhead can make it slower compared to simpler protocols like UDP.