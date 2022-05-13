# Network Address Translation (NAT)
- Designed to address the shortage of IPv4 addresses
  - IPv4 are either pubicly routable or fall within private address space
    - Publicly routable addreses are assigned by a central agency and regional agencies -> assign them to Internet Service Providers (ISP) -> ISPs allocate them to business or consumer end-users. => must be unique
    - Private addresses (such as 10.0.0.0 range) can be used in multiple places, but not routable over the internet
- To give internet access to private devices...we need NAT => ***NAT translates private IP addreses into public IP addresses*** so packets can flow over public internet -> then translate back in reverse, so that internet-based hosts can communicate back with these private services
- Provides some security benefits
- **IPV4 only**...IPv6 has many addresses and doesn't need translation. 
<br>

## Static Network Address Translation 
#### This is how AWS Internet gateway works
- 1 private : 1 (fixed) public (IGW)
  - Gives the private address access to the public internet in both directions (how Gateway in AWS works)
  - Use when certain specific private IP addresses need access to the internet using a public IP and where these IPs need to be consistent. 
 
Looking at the image...
- Private IPs can't be routed over to public internet (CatAPI)
- NAT table stores a one-to-one device mapping between private IP and public IP.
- Any enabled private device will have a dedicated allocated public IPv4 address
  - The public IPv4 is not configured on the device ~ just an allocation.
  - At no point are the private devices configured with a public IP.
- **Outgoing traffic:** source IP is translated from private address to corresponding public IP.
- **Incoming traffic:** destination IP is translated from allocated public address through to the corresponding private IP.

![NAT_Static](https://user-images.githubusercontent.com/72099370/167988190-88dc266a-faea-4aae-a4ac-8c3f7285d230.png)

<br>

## Dynamic Network Address Translation
- 1 private : 1st avaialble public
- Pool of public IPs to use and allocate as needed => when private IPs attemps to use internet for something, dynamic NAT can take large number of private IPs to have internet access via public IPs.
  - ...however, if you have less public IPs than private IPs, you want to be efficient. 

![NAT_Dynamic](https://user-images.githubusercontent.com/72099370/167988217-02f4a48d-0ed2-4dbf-ad78-a7254c29739e.png)

<br>

## Port Address Translation (PAT)
- Many private : 1 public (NATGW)
  - probably what our home router does => overloading using PAT with many devices.
- Uses ports to identify individual devices.

![PAT_PortAddressTranslation](https://user-images.githubusercontent.com/72099370/167988286-df0401d2-d8cf-4d11-b5eb-ea68f7572278.png)
