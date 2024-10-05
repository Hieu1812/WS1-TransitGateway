+++
title = "Transit gateway route table and check for the result"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

For Transit Gateway Attachment to work, we need to create a route table for them. 
In this section, you will create a route table and check if the systems are connected to each other or not.

1. Access Transit Gateway route table
  ![Launch Template](/images/anh/tsgwrtb.png)
2. Select Transit Gateway and Create Transit Gateway route table.
  ![Launch Template](/images/anh/createtsgwrtb.png)
3. Select route table which just created -> Associatons -> Create Associations
  ![Launch Template](/images/anh/association.png)
4. Select Attachment -> Create Associations
  ![Launch Template](/images/anh/association1.png)
  - Do the same with other attachments
5. Continue with that route table -> Propagations -> Create Propagations
  ![Launch Template](/images/anh/propagation.png)
6. Select Attachment -> Create Propagations
  ![Launch Template](/images/anh/propagation1.png)
  - Do the same with other attachments

Next, we going to config route table to add route from transit gateway

1. Access route table -> select route table -> routes -> edit routes
  ![Launch Template](/images/anh/rtb.png)
2. With Public route table, we add route and config it
  - Fill IP address **172.12.0.0** 
  - Select Transit Gateway.
  - Select Transit Gateway which is created.
  - Save changes 
  ![Launch Template](/images/anh/rtb1.png)
3. With Private route table, we add route and config it.
  - Fill IP address **0.0.0.0/0** 
  - Select Transit Gateway.
  - Select Transit Gateway which is created.
  - Save changes 
  ![Launch Template](/images/anh/rtb2.png)
  - Do the same with other private route table

Test the connection between VPCs

- We will SSH from EC2 public to EC2 private to test the connection between private EC2
  ![](/images/anh/sshtopri2.png)
 ```
 ssh -i "file-name" ec2-user@<private ec2 ip>
 ```
- After accessed into EC2 private 1 we ping to EC2 private 2 and 3
  ![](/images/anh/pingtopri1.png)
  ![](/images/anh/pingtopri3.png)

Congratulations. The EC2 Instances in your VPCs were able to connect through the Transit Gateway.
For monitor transit gateways, you can reference this article [CloudWatch metrics](https://docs.aws.amazon.com/vpc/latest/tgw/transit-gateway-cloudwatch-metrics.html)
