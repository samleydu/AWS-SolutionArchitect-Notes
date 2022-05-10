My notes for Adrian Cantrill's AWS Solutions Architect course via https://learn.cantrill.io/
<br>
This is solely for me to study for AWS certification. Not to be distributed.

## What is Cloud Computing?
According to the National Institute of Standards and Technology (NIST)'s definition...<br>
5 essential characteristics:
1. On-demand self-service: "...can provision capabilities as needed *without requiring human interaction*"
2. Broad network access: "Capabilities are available over the *network* and accessed through *standard mechanisms*..."
3. Resource pooling: "There is a sense of *location independence*... no *control* or *knowledge* over the exact *location* of the resources" / "... Resources are *pooled* to serve multiple consumers using a *multi-tenant model*"
4. Rapid elasticity: "Capabilities can be *elastically provisioned* and *released* to scale *rapidly* outward and inward with demand." / "To the consumer, the capabilites available for provisioning ofen *appear* to be *unlimited*"
5. Measured service: "resource usage can be *monitored*, *controlled*, *reported*...AND *BILLED*"

![image](https://user-images.githubusercontent.com/72099370/167738255-212dcbae-6aae-4e43-ad75-e01d03ec9035.png)

<br>
<br>

## Public vs Private vs Multi vs Hyrbrid Cloud
- **Public**: using 1 public cloud <br>
AWS or Azure or Google Cloud 
- **Private**: using on-premises *real* cloud <br>
meeting the 5 essential characteristics 
- **Multi**: using more than 1 public cloud <br>
deploy 1/2 in 1 public cloud & half in the other || use 3rd party tool || etc.
- **Hybrid**: Public and Private cloud <br>
  - public + private of same vendor as 1 unified platform
  - *NOT* public cloud + legacy on-premises => (this means hybrid env or network)
![image](https://user-images.githubusercontent.com/72099370/167738904-a57bcd8d-98f5-4435-8b47-de15488b7d90.png)

<br>
<br>

## Cloud Service Model
![CloudServiceModel](https://user-images.githubusercontent.com/72099370/167739717-f03ae8bb-4015-41cd-aaed-c1a0ffe074c7.png)


