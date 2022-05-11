# Data Link

- Identificable devices
- Media access control (sharing)
- Collision detection
- Unicast 1:1 vs. Broadcase 1:ALL
- Switches - like HUBs with super powers (L2)

## Frame
- Layer 2 uses Layer 1
  - L2 can be transmitted onto the shared physical medium by L1 => converted into voltages radio frequency or light - sent across the medium - recevied by other devices connected to that medium
- L2 uses frame: a format to send info over L2 network
- L1 handles physical transmission & reception to/from shared medium => doens't understand frame...only transmitting it

### Components of a frame / Encapsulation process:
1. PREAMBLE: starts frame delimiter - allows devices to know it's the start of frame to identify various part of the frame 
2. DESTINATION (and SOURCE MAC ADDRESSES): frame(s) can be sent to specific/every device on a network (every device = broadcast) - allows MAC address to receive replies
3. ETHERTYPE (ET): to specify which last 3 protocol is putting its data inside a frame => just like L2 uses L1 to move raw bitstream data acrross shared phy.med. while L3 uses L2 for device-device communicationon local network
4. PAYLOAD: contains data that frame is sending (data is generally provided by L3 & protocol indicated by ET)
5. FRAME CHECK SEQUENCE (FCS): identify any errors in the frame - simple CRC check: allows destination to check if corruption has occurred
 
**MAC HEADER** (2 & 3): control frame destination -> indicate source -> specify its function

![Layer2_DataLink-Frame](https://user-images.githubusercontent.com/72099370/167742559-2e24ddf2-a620-475b-bf57-8c1ec1a0af99.png)

<br> 

## Carrier Sense, Multiple Access / Collision Detection (CSMA/CD)

### Problem with using a purely L1 network implementation:
![Layer2_DataLink-CSMA-CD(0)](https://user-images.githubusercontent.com/72099370/167743579-cdfc710e-bad1-41f1-99a3-4301785f2bd1.png)

### L2 working with L1: 

![Layer2_DataLink-CSMA-CD](https://user-images.githubusercontent.com/72099370/167743661-91428db9-1fde-4511-b172-f0b9ad1a5d44.png)

<br>

## L2 using a HUB vs. a Switch

### using a HUB
![Layer2_UsingAHub](https://user-images.githubusercontent.com/72099370/167746081-e448d169-e384-40fb-a1e0-02dc655ec204.png)

### using a Switch
![Layer2_UsingASwitch](https://user-images.githubusercontent.com/72099370/167746113-ab61fe0a-ee6f-4502-be35-16c679ac31c7.png)
