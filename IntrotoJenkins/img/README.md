# Introduction to Jenkins
Jenkins is used to automate building, testing and deploying applications, streamline the development lifecycle.

### Installing Jenkins
Firstly, I update package repositories, installed jdk and installed jenkins
![](./1.png)

![](./2.png)

![](./3.png)

![](./4.png)
 I confirmed that jenkins was running and is up and running
![](./5.png)

I then opened port 8080 on my EC2 instance Security group, since jenkins listens on port 8080
![](./6.png)

On the jenkins instance, I checked to know the admin password
![](./7.png)

I inputed the jenkins ip address on my web browser and filled in the password gotten previously
![](./8.png)

I installed the suggested plugins
![](./8a.png)

and created the first admin user
![](./8b.png)

This is the newly created admin profile on the jenkins console
![](./9.png)
