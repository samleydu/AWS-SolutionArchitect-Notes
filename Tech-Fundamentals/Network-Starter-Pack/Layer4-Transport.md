# Layer 4 - Transport

<br>

## Layer 3 Problems
### Why we need L4!
![Layer3_Problems](https://user-images.githubusercontent.com/72099370/167973559-b1e5a0aa-a15a-44d7-a243-af46541ea75b.png)

<br>

## TCP and UDP - L4 adds these protocols
Both runs on top of IP & add a collection of features depending on which is used.
- Transmission Control Protocol (TCP)
  - Connection-oriented architecture: bi-directional channel of communications
  - High-level use for reliability, error correction and ordering of data
  - Used for most important app layer protocols: HTTP, HTTPS, SSH, etc.
- User Datagram Protocol (UDP)
  - Faster than TCP: no reliable delivery of data == less reliable
  - All about performance
  
![Layer4_TCP UDP](https://user-images.githubusercontent.com/72099370/167973897-f758d06a-fc7f-4c29-9919-4ab747b1a464.png)

<br>

## TCP Segments
Placed inside packets and transmitted by one network stack specifically by L4 protocol, TCP in this case.
- **SOURCE PORT & DESTINATION PORt:** gives TCP/IP protocol the ability to have multiple streams of conversations at the same time between 2 devices
  - Allow the internet to function flexibly 
  - Each conversation is a unique combination of src/dest IP/port.
  - Example: Opening AWS web interface communicates from port of local machine to port on AWS servers, TCP port 443 which is HTTPS. AWS can have multiple streams of communication to their servers.
  - Example 2: Ports allow multiple streams of communications from local machine to AWS, Netflix, other websites. 
  - Example 3: SSH and HTTPs can exist on the same EC2 instance. Multiple SSH connections open to the same EC2 instance.
- **SEQUENCE NUMBER:** a way of uniquely identifying a particular segment within a particular connection so both sides can make observations about it (using ACKNOWLEDGMENT)
  - Unique.
  - Increments by each segment that sent it. 
  - Can be used for error correction if things need to be re-transmitted .
  - Can be used ensure when IP pakcets are received, TCP segments are pulled out so they can be correctly ordered.
- **ACKNOLWEDGEMENT:** is the way that one side can indicate that it has received up to & including a certain sequence number.
  - Every segment transmitted **needs** to be acknowledged.
  - If device is transmitting TCP segment1+2+3+4, then the other device needs to acknoweldge it's received the same segments.
- **FLAGS 'N' THINGS:** allows various controls over the  TCP segments and the wider connection.
  - 9 bits.
  - Close the connection or synchronize sequence numbers.
  - Data-offset, some reserved space.
- **WINDOW:** defines number of bytes that you indicate you are willing to receive between acknowledgements.
  - Lets receiver controls the rate at which sender sends data:
    - Once reached, sender will pause until you acknowledge that amount of data => how control is implemented.
  - Smaller window: additional levels of control over how quickly data is sent.
  - Larger window: more efficient because header of TCP segment takes up an amount of space => smaller windows = more headers.
- **CHECKSUM:** error checking  
  - TCP layer is able to detect errors & arrange for retransmission of data as required
- **URGENT POINTER:** allows client and server to have separate processing => control traffic takes priority within the communication
  - Latency-sensitive protocols transferring can use this field: FTP and Telnet...
  - Example: Data transfer application where 99% is transferring and 1% is controlled traffic - communication between client and server coordinating the actual data transfer. 

![Layer4_TCP_Segments](https://user-images.githubusercontent.com/72099370/167974375-61e06692-e24d-49e9-823e-f048433992b8.png)

<br>

## Transmission Control Protocol (TCP) architecture
Looking at the image...
- Two separate sets of segment: tcp/23060 -> tcp/443 **and** tcp/443 -> tcp/23060 => two set of rules on a network ACL within AWS:
  - One rule for initiating so laptop -> server 
  - Other rule for response so server -> laptop
- Ephemeral/high ports: port range that client picks as the source port
  - Often needs to add firewall rules allowing all of this range back to the client
   
![Layer4_TCP](https://user-images.githubusercontent.com/72099370/167977350-1f9702a9-87ee-4587-9021-8664d6bf504a.png)

<br>

## TCP Connection 3-way Handshake
Important that both sides know the sequence numberthat each will be starting with, because it's this unique sequence number that will be used to acknowedge the receipt of any data. 
![Layer4_TCP_3WayHandshake](https://user-images.githubusercontent.com/72099370/167980171-4419ded5-2174-46be-9ef9-091efc79f4ed.png)

<br>

## Sessions & State

#### stateless vs. stateful firewall: important to understand
- Stateless: doens't understand state of connection
  - 2 rules: outbound and inbound.
  - Network access control list (ACL) in AWS.
- Stateful: understands the state of TCP segment
  - Initial traffic and response = one thing - both allowed.
  - Extension of what stateless firewall can achieve.
  
Looking at the image...

- We want to add security to laptop:
  - What rules to add?
  - What types of traffic to allow **from** where and **to** where, in order that this connection will function without issues?
  
![Layer4_TCP_Session State](https://user-images.githubusercontent.com/72099370/167984840-4cc12536-d1af-42fe-bc65-322a00e3e1f4.png)

<br>

## Summary
- L4 uses TCP segments and concerns itself with IP addresses and port numbers. 
- Strictly speaking, concept of session or ongoing communication between two devices are of L5.
- Stateless vs. stateful and how they change how to create security rules.
- At this point (L4) in the OSI, we have a stable consistent communication channel which is bi-directional between 2 different devices / we will build on this in L6 and L7 which will allow us to add encryption and various application layer protocols.

