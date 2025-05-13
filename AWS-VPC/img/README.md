# AWS VPC
In this project, I explored the fundamental components of VPC infrastructure, including subnets, gateways and routing tables.

Firstly, I created a VPC

![](./1.png)

![](./2.png)

Then I created a public subnet
![](./3.png)

I also created an Internet gateway which was in a detached state
![](./5.png)

I then attached the Internet gateway to my vpc
![](./6.png)

I created a public route table
![](./7.png)

In the public route table, I added a route for the Internet gateway to accept traffic from anywhere
![](./8.png)
![](./9.png)

Then I associated my public subnet with the public route table
![](./10.png)

I created a private route table
![](./11.png)
I associated my private subnet with the private route table
![](./12.png)

I created a nat gateway in the public subnet
![](./13.png)
Finally, I added a route to the nat gateway in the private route table
![](./14.png)

# VPC PEERING
I configured VPC peering to enable comunication between resources in different VPCs

Firstly, I created a requester VPC
![](./15.png)

Then I created an accepter VPC
![](./16.png)
![](./17.png)

I established the vPC peering connection by accepting the connection request
![](./18.png)

I created a route table for the requester VPC and added the CIDR of the accepter VPC to the route table
![](./19.png)
![](./20.png)

Then, I created an accepter route table and added the CIDR of the requester VPC to the route table

![](./21.png)

![](./22.png)

