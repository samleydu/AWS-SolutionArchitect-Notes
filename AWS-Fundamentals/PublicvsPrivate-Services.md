# Public vs Private Services 

Looking at the image...

- AWS PUBLIC zone
  - Between public internet zone and AWS private zone
  - Where AWS public services operate from
  - Accessible from anywhere with a public internet connection
- AWS PRIVATE zone
  - Only accessible if you allow it
  - Can attach internet gateway to VPC
  - Communicate with public service using AWS public zone

Looking at the image...

AWS Private Zone:
- Internet gateway attached to VPC allowing private zone resources to access the public internet as long as EC2 has an allocated public IP address.
  - Allows access to public AWS services such as S3 **but** the data doesn't touch public internet at any point
  - Communicates with the public service using AWS Public Zone.
- It's possible to give private resources such as EC2 instances of public IP address -> allows the resource to be accessed from the public internet.
  - ...by projecting the EC2 instance to the public zone so all/part of the instance can be communicated with from the public internet

![PublicvsPrivateServices](https://user-images.githubusercontent.com/72099370/168201861-306bb1db-238f-4105-927b-311653fd5c72.png)
