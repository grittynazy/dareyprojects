# Jenkins Freestyle Project
In Jenkins, a job is a unit of work or a task that can be executed by the Jenkins automation server

## Creating first build job
On the dashboard, I clicked on new item and created a freestyle project named my-first-job
![](./1.png)

I created a new repository on Github and copied the code
![](./8.png)

I then inserted the github repo link in jenkins 
![](./2.png)

I changed the branch from master to main and started the build
![](./3.png)

This is the status of the manual build
![](./4.png)

I then set the build trigger on Jenkins to automatically run a build when a change is made to the repo, comitted and pushed
![](./5.png)

I configured Github webhooks to make sure Jenkins is receiving webhook POST requests from GitHub
![](./6.png)

After configuring the webhooks, I made a change to the README file, and a build was automatically run in Jenkins
![](./9.png)

![](./7.png)