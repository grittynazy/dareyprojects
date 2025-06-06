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

## Creating first build job
On the dashboard, I clicked on new item and created a freestyle project named my-first-job
![](./10.png)

I created a new repository on Github and copied the code
![](./17.png)

I then inserted the github repo link in jenkins 
![](./11.png)

I changed the branch from master to main and started the build
![](./12.png)

This is the status of the manual build
![](./13.png)

I then set the build trigger on Jenkins to automatically run a build when a change is made to the repo, comitted and pushed
![](./14.png)

I configured Github webhooks to make sure Jenkins is receiving webhook POST requests from GitHub
![](./15.png)

After configuring the webhooks, I made a change to the README file, and a build was automatically run in Jenkins
![](./16.png)

![](./18.png)