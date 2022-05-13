# Distributed Denial of Service (DDoS)
Distributed Denial of Service (DDOS) attacks are effective at disrupting web applications no matter their size.

They are generally initiated from networks of compromised machines known as Botnets.

They come in 3 common types...
- Application Layer
- Protocol Attacks
- Volumetric Attacks

Some descriptions:
- Attacks designed to **overload** websites
- **Compete** against 'legitimate connections'
- **Distributed** - hard to block individual IPs/Ranges
- Often involve large armies of compromised machines (botnets)

<br>

## How a valid application architecture should look like:
![DDOS_Normal](https://user-images.githubusercontent.com/72099370/167539784-b2e5b07c-da94-454f-a81d-c645ab827b63.png)

<br>

## Types of attack:
#### 1. Application Layer - HTTP Flood
- Take advantage of the imbalance of processing between client and server 
<br> => easy to request webpage but often complex for server to deliver that page, so multiplying load differences by billions can cause devastating attack

![DDOS_ApplicationLayerAttack](https://user-images.githubusercontent.com/72099370/167539298-9d53d148-ddf2-4f7b-a3f9-b58de3c874b4.png)



#### 2. Protocol Attack - SYN Flood 
- Take advantage of connection-based nature of requests. Normally, connection is initiated through 3-stage-handshake 
<br> => spoof source IP address & initiate connection attempt with server. Server tries to perform step2 of handshake but can't contact source address because it is spoofed. The hand will wait for a specified duration consumes network resources. 

![DDOS_ProtocolAttack](https://user-images.githubusercontent.com/72099370/167541058-fb443075-5c03-4fd0-bf9f-1c7f0cc91e6e.png)
#### *3-way Handshake:*
![3-way-handshake](https://user-images.githubusercontent.com/72099370/167541618-ee35c683-4e82-415e-97a4-0ec35f5f4640.jpg)

#### 3. Volumetric/Amplification - DNS Amplification
- Relies on how certain protocols such as DNS (DNS resolution) only takes small amount of data to make a request but can deliver a large amount of data
<br> => make requests to DNS servers of large # of independent requests but source address is spoofed to be the actual IP address of the website. The DNS servers now respond to what they see as legit requests and overwhelm the server.

![DDOS_VolumetricAttack](https://user-images.githubusercontent.com/72099370/167541065-8e0cbdd8-49df-4975-9ae6-23be1bc20944.png)


