# Layer 3 - Network
- Requires one or more L2 networks to function.
- Job is to get data from one location to another: from source to destination (inter-networking)
  - Example: data being moved from server to host video through local device that you are watching / data is being moved across internet when streaming Netflix

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
    - IP packets are moved from source to destination across the internet through many intermediate networks. 
    - Example: The device you are using has an IP address, as well as the server running this website: IP is being used to send requests from your local network across the internet, to this website, and back again. 
  - **Routers:** L3 devices that move packets of data across different networks.

![Layer3_L2toL3-BuildingaCommonL3Network](https://user-images.githubusercontent.com/72099370/167758496-b80947af-bd36-43d9-9344-e2fec62965f3.png)
