# Layer 4 - Transport

<br>

## Layer 3 Problems
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
- **SOURCE PORT & DESTINATION PORt:** gives TCP/IP protocol the ability to have multiple streams of conversations at the same time between 2 devices
  - Allow the internet to function flexibly 
  - Each conversation is a unique combination of src/dest IP/port.
  - Example: Opening AWS web interface communicates from port of local machine to port on AWS servers, TCP port 443 which is HTTPS. AWS can have multiple streams of communication to their servers.
  - Example 2: Ports allow multiple streams of communications from local machine to AWS, Netflix, other websites. 
  - Example 3: SSH and HTTPs can exist on the same EC2 instance. Multiple SSH connections open to the same EC2 instance.
- **SEQUENCE NUMBER:** a way of uniquely identifying a particular segment within a particular connection so both sides can make observations about it (using ACKNOWLEDGMENT)
  - Unique.
  - Increments by each segment that sent it. 
  - Can be used for error correction if things need to be re-transmitted 
  - Can be used ensure when IP pakcets are received, TCP segments are pulled out so they can be correctly ordered.
- **ACKNOLWEDGEMENT:** is the way that one side can indicate that it has received up to & including a certain sequence number.
  - Every segment transmitted **needs** to be acknowledged
  - If device is transmitting TCP segment1+2+3+4, then the other device needs to acknoweldge it's received the same segments.
- **FLAGS 'N' THINGS:** allows various controls over the  TCP segments and the wider connection
  - 9 bits
  - close the connection or synchronize sequence numbers 
  - Data-offset, some reserved space.
- **WINDOW:** defines number of bytes that you indicate you are willing to receive between acknowledgements
  - Lets receiver controls the rate at which sender sends data
    - Once reached, sender will pause until you acknowledge that amount of data => how control is implemented

![Layer4_TCP_Segments](https://user-images.githubusercontent.com/72099370/167974375-61e06692-e24d-49e9-823e-f048433992b8.png)
