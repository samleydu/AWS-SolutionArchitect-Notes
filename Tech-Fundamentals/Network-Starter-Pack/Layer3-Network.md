# Layer 3 - Network
- Requires one or more L2 networks to function.
- Job is to get data from one location to another: from source to destination (inter-networking).
  - Example: data being moved from server to host video through local device that you are watching / data is being moved across internet when streaming Netflix.
- Internet protocol = L3 protocol.

<br>

## L2 => L3 - Building a Common L3 Network
### Why do we need L3?
Looking at the image...
- LAN1 and LAN2 are isolated: local devices can communicate on local L2 network.
  - How can we connect these two networks? 
    - Point to point link across entire US is expensive and not scalable in large quantity.
    - Each L2 network uses shared L2 protocol (ethernet here) - and if we want networks to communicate with each other, it need the same L2 protocol. What to do? <br>
=> L3 can spam multiple different L2 networks.

- L3 can be added onto one or more L2 networks: adds internet protocol (IP).
  - **IP addresses**: cross-networking addresses that can be assigned to devices to communicate across networks using routing. 
    - Example: The device you are using has an IP address, as well as the server running this website: IP is being used to send requests from your local network across the internet, to this website, and back again. 
  - **Routers:** L3 devices that move packets of data across different networks.
    - IP packets are moved from source to destination across the internet through many intermediate networks. 
    - Routers _encapsulate a packet inside of an ethernet frame_ for that part of the journey over that local network:
      - When the packet needs to be moved into a new network, the frame is removed and new one is added around the same packet.

![Layer3_L2toL3-BuildingaCommonL3Network](https://user-images.githubusercontent.com/72099370/167758496-b80947af-bd36-43d9-9344-e2fec62965f3.png)

<br>

## IP - Packet Structure
#### **IP Packets:** contains data to-be-moved with source and destination address
  - Different from frame: frame = local. 
  
![Layer3_IP-PacketStructure](https://user-images.githubusercontent.com/72099370/167762126-cad577af-4c99-4866-8fa0-a5138247fc0f.png)

### IPv4 Fields:
- **SOURCE IP ADDRESS:** generally the device IP that generates the packet.
- **DESTINATION IP ADDRESS:** intended destination IP for the packet.
- **PROTOCOL:** contans data provided by L4 as L3 is just IP
  - Network stack at the destinatio. L3 component of that stack to know which L4 protocol to pass data into
  - Example protocols: ICMP, TCP, or UDP. If storing TCP data inside packet, value = 6 / ICMP (pings) value = 1 / UPD = 17.
- **DATA:** takes up bulk of space within a packet
- **TIME TO LIVE (TTL):** defines how many hops packet can go through (the many different intermediate networks between source and destination). 
  - Stops packet from looping around forever.
  - If packet can't reach destination, discard if max number of hops is reached.
### IPv6 Fields:
 - Similar to IPv4 / some fields matter less as they are functional
 - SOURCE and DESTINATION IP ADDRESSES are **bigger** so takes up more storage space in packet => more possibel IPv6 addresses 
 - **HOP LIMIT** instead of TTL:  similar functionality
### Summary of packets' journey: 
- Packets contain data carried from L3 protocols...
- IP protocol implementation on routers moves packets between all networks from source to destination...
- As packets move through each intermediate L2 network, it will be inserted or encapsulated in a L2 frame specific for that network
  - A packet might exist in 10s of different frame throughout its route to its destination
 
 

