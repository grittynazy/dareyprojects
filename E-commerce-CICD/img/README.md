# E-Commerce Application CI/CD Pipeline

In this project, I set up a simple Node.js/Express application that handles basic E-commerce operations and implemented unit tests for my API. I created a simple React application that interacts with the backend API. I ensured the frontend has basic features like product listing, user login, and order placement. I then wrote a Github Actions workflow for the backend and frontend that installs dependencies, runs tests, and builds the application. I created docker files for both the backend and frontend and modified my github actions workflow to build docker images. I then configured Github Actions to deploy the docker images to AWS

Firstly, I created a Github repository
![](./1a.png)

Then I cloned the repository into my local machine, created a backend directory and created a server.js file in it
![](./1.png)
![](./2a.png)
![](./2b.png)

I also created the test directory and an app.test.js file
![](./3.png)

I then created a react frontend and ran all the necessary commands
![](./4a.png)
![](./4b.png)

This is the app.js file
![](./5a.png)
![](./5b.png)

I added the necessary tests for the application
![](./42.png)
![](./48.png)
![](./49.png)
![](./50.png)
![](./51.png)

I then created the .github/workflows directory which had 3 workflows: backend.yml, frontend.yml and deploy.yml workflow files
![](./6.png)

![](./43a.png)

![](./43b.png)

![](./43.png)

I then created Dockerfiles for both backend and frontend 
![](./10.png)

![](./11.png)

![](./12.png)

I tested the backend locally and it opened on the browser. I also opened the product listing page successfully, same with the login and order pages
![](./13.png)
![](./14.png)
![](./15.png)
![](./16.png)

I then built the frontend docker image and tried to open the link on the browser
![](./17.png)
![](./18.png)

Then I updated my src/app.js file
![](./20.png)
![](./21.png)
![](./22.png)

I then created a docker compose file and ran the container
![](./19.png)
![](./23.png)

My e-commerce app was tested locally and everything seemed fine
![](./26.png)

I then logged into docker and pushed my images to docker hub
![](./29.png)

![](./30.png)

I created an AWS EC2 instance for the deployment and adjusted the security group to listen to port 3000, 5000, 22 and 80

![](./47.png)
![](./32.png)

I inputted the following secrets in Github so my deploy.yml file can run successfully

![](./35.png)

I then added, committed and pushed my changes and the e-commerce application got automatically deployed to AWS EC2
![](./36.png)

![](./37.png)

![](./38.png)

![](./40.png)



