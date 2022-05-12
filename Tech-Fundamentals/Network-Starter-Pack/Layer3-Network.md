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
 
 <br>
 
 ## IP Addressing (v4) - IPv4
 - IP addressing is what identifies a device which uses L3 IP networking. 

![Layer3_IPAddressing-IPv4](https://user-images.githubusercontent.com/72099370/167764583-b5ee6f75-697e-4287-8ee0-91b1c60e0cd5.png)

Looking at the image...
- Pure network connectivity POV: if you have valid IPv4 address, you can send packets to 133.33.3.7
  - The IPv4 address will at least start to route to this 133.33.3.7
    - Possible blocks in the way: firewalls, security restrictions, or IP is offline **but** packets will move over the internet on its way to 133.33.3.7
- **All** IP addresses are formed in 2 different part: 133.33/./3.7
  - Network part: which IP network the IP address belongs to (133.33)
    - If network parts match: same IP network - devicces are local. If not, devices are remote.  
  - Host part: represents hosts on that network (3.7) - i.e. a laptop
- **Static IP:** IP addresses assigned by humans.
- **Dynamic IP:** IP addresses assigned by machines - server software Dynamic Host Configuration Protocol (DHCP) running on network

<br>

## Subnet Mask
Subnet masks are used to determine which part of an IP address is the network apart and which is the host poart.
- 2 IP addresses with same network part: they are on the same IP network (local)
  - This is essential so that machine can identify when it can send data directly on the same local network or when IP routing needs to be used to transfer packets across different intermediate networks. 
![Layer3_SubnetMask](https://user-images.githubusercontent.com/72099370/167969551-12dfba68-6b29-404c-b236-22ba1a01374f.png)

<br>

## Route Tables & Routes
- Every routers has at least 1 route table
- Route tables can be statically populated, or there are protocols such as Border Gateway Protcol (BGP) which allow routers to communicate with each other to exchange networks they know about => the core of the internet functions
![Layer3_RouteTables Routes](https://user-images.githubusercontent.com/72099370/167970693-e75b1f84-0706-44d1-8ab1-cb0a1c153c06.png)

Looking at the image...
- ISP router is forwarding the packet through to AWS router at L2
  - Packet does not change but frame does.
  - It has AWS MAC address as its destination
    - How is the MAC address determined? => **Address resolution protocol.**
