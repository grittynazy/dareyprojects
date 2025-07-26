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

I implemented matrix builds to test across muktiple versions in order to increase efficiency
![](./24.png)

#### Adding Code Analysis Tools
I also integrated code analysis tools into the Github Actions workflow
![](./25.png)

#### Configuring linters and Static code Analysis
I ensured my repository included configuration file for .eslintrc
![](./26.png)

I then pushed the cchanges to github
![](./17.png)

#### Automated Versioning with Github Actions
I implemented automated versioning to increment version numbers automatically based on code changes. The action below will automatically increment a patch version and create a new tag each time changes are pushed to the main branch
![](./27.png)

#### Automating Releases
I setup my workflow to create a new release whenever a new tag is pushed to the repository
![](./28.png)

I had to change the settings on my github repo to allow workflows have read and write permissions and allow github actions to create and approve requests.
![](./31.png)

I pushed my commit with the version tag
 and the pipeline ran successfully
![](./29.png)

![](./32.png)