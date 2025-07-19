# TERRAFORM EC2 INSTANCE AND AMI CREATION

In this project, I used terraform to automate the creation of an EC2 instance on AWS and then created an AMI from that instance

Firstly, I confirmed the prerequisites which is to have aws installed, and configured. 

![](./1.png)
![](./2.png)
![](./3.png)

I checked my installed terraform and it was out of date, so i updated the packages on my machine and upgraded the terraform version
![](./4.png)
![](./5.png)
![](./6.png)

I made a directory for my terraform project and created a main.tf file. In this file I wrote a script to create an EC2 instance, specifying instance type, ami and tags. I extended this script to include the creation of an ami from the created ec2 instance
![](./7.png)

I initialized the terraform project using terraform init and I validated the correctness of this script using terraform validate but I ran into an error
![](./15.png)
![](./12.png)

The error came about because I used the resource aws_ami, which is used for registering an AMI manually, usually from an existing EBS snapshot, not from an EC2 instance. So I changed the resource from aws_ami to aws_ami_from_instance
![](./13.png)

I then ran terraform validate again and it worked fine
![](./14.png)

I confirmed the resources that will be created by the execution of this script using terraform plan
![](./11.png)

I then applied the configuration using terraform apply and confirmed the setup on my ec2 console
![](./8.png)
![](./9.png)

![](./10.png)

Then I cleaned up all the resources created by the script
![](./17.png)
![](./18.png)


