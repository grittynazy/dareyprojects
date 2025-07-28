# Setting Up Ansible on a Linux Server
In this project, I installed and configured ansible on a Linux server, allowing the automation of tasks and effective management of servers

Firstly, I updated my package repository, then I installed ansible on the control node which was my local machine. I then generated an SSH key pair on the control node, sshed into each target node and pasted the public key in the authorized keys file. I did this because ec2 instances which were my target nodes do not have passwords by default. I then tested ssh without a password. Then I created a directory for ansible configuration, created an inventory file and added the target machine details to the inventory. Then I tested ansible connectivity to the target machines and got a pong response. I also ran simple adhoc commands like checking the uptime of the target machines, checking the disk usage and creating a file in the target nodes. I then confirmed the creation of this file from the target nodes
![](./1.png)

![](./2.png)

![](./3.png)

![](./4.png)

![](./5.png)

![](./6.png)

![](./14.png)

![](./7.png)

![](./8.png)

![](./9.png)

![](./10.png)

![](./11.png)

![](./12.png)

![](./13.png)

I then created an ansible playbook to automate user creation. The playbook included group and ssh key configuration. I then verified user creation and tested ssh access for newly created users.

![](./15.png)

![](./16.png)

![](./17.png)

![](./18.png)

![](./19.png)

![](./20.png)

![](./21.png)

![](./22.png)

![](./23.png)

![](./24.png)

