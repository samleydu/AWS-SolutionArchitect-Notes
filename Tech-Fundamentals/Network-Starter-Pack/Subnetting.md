# IP Addressing & Subnetting
This part of the Network fundamentals series steps through IP addressing (IPv4) vs IPv6 Addressing and IP subnetting
- IPv4 Class Based Addressing https://tools.ietf.org/html/rfc791
- IPv4 Private Addressing https://tools.ietf.org/html/rfc1918

<br>

## IPv4 Addressing & Subnetting / Address Space 

- All public IPv4 addressing is allocated...
- Part of the address space is private ...can be used/reused freely

Looking at the image...
- All of these addresses are publicly routable with few exceptions.
- Class A generally used  for huge networks.
  - First octet denotes the network with remaining octets available for hosts or subnetting.
  - Generally allocated to regional authorities and they manage them and allocate them out to any organization who requests and can justify addresses in this range.
- Class B typically for larger businesses.
  - First 2 octets are for the network ~ last 2 are for organization to assig to devices or to subnet into smaller networks.
- Class C historically used for smaller businesses who required an IPv4 presence, but weren't large enough for B or A addressing.
  - First 3 octets denote the network and remaining is available for hosts or subnetting.
- Class D is for multicast and class E is reserved. 

Within this public IPv4 space, certain networks are reserved for private use (use however you want) and aren't routable across the public IPv4 internet => can only be used for private networks or cloud platforms such as AWS

![IPv4_AddressSpace](https://user-images.githubusercontent.com/72099370/168195973-a93ebfe2-f67e-466e-bb42-7d54bfff74f5.png)

<br>

## IPv4 versus IPv6 Address Space
![IPv4-6_AddressSpace](https://user-images.githubusercontent.com/72099370/168197491-4d799668-139b-45c4-aaa7-5f4ac8e61281.png)

<br>

## IP Subnetting
- The larger prefix value the smaller the network

![IP_Subnetting](https://user-images.githubusercontent.com/72099370/168197886-1f8fadd5-a2c7-4bdb-86f4-1e1eb91c121c.png)
![IP_Subnetting-cont](https://user-images.githubusercontent.com/72099370/168198723-20e9c6a6-d928-4d2c-8f7b-e22de3d84e0e.png)

