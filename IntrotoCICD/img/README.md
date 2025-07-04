# Introduction to Continuous Introduction and Continuous Deployment

Firstly, I initialized a github repository, created it and cloned it to my local machine
![](./1.png)

![](./2.png)

I initialized a node.js project, created a simple server using Express.js to serve a static web page and added the code to the repository and pushed it to Github. I also added automated tests for my application using Mocha and chai
![](./3.png)

![](./4.png)

![](./5.png)

I created a .github/workflows directory and added a workflow file nodejs.yml
![](./6main.png)

This is my index.js file
![](./7.png)

I created a test folder and an app.test.js file
![](./8.png)

I tested my app and it passed
![](./9.png)

I pushed the changes to github and the job ran successfully

![](./23.png)

I created an EC2 instance, cloned my app repository into it and tested the app
![](./21.png)

![](./10a.png)

![](./11.png)

I created a key in my local machine, copied the publick key and added to github secret
![](./12.png)

![](./13.png)

![](./14.png)

I also created a deployment workflow file for deployment to AWS and pushed the changes to github
![](./15.png)

![](./16.png)

![](./17.png)

I made some changes to the code to see if the pipeline would run smoothly
![](./18.png)

![](./19.png)

I tested the app locally first and then pushed the changes to github

![](./9b.png)
![](./22.png)

The changes reflected on AWS
![](./20.png)



