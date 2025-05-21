# Working with Docker Images
Docker images are the building blocks of containers.  
Docker Hub is a cloud based registry that hosts a vast collection of Docker images

I tried to find the ubuntu image on Docker Hub
![](./1.png)

I downloaded the official ubuntu image to my local machine and viewed a list of the images on my machine
![](./2.png)
![](./3.png)

I created a Dockerfile by specifying a base image, defining the working directory, copying files, installing dependencies and configuring the runtime environment
![](./4.png)

I created an index.html file in thesame location as the dockerfile
![](./5.png)

![](./6.png)

I created the image and tagged it using the docker build command and confirmed the image creation
![](./7.png)
![](./8.png)

I then ran a container based on the custom NGINX image I earlier created
![](./20.png)

I tried accessing the site and wasn't able to
![](./11.png)

I then editted the inbound rules of my EC2 instance and opened port 8080 to anywhere
![](./10.png)

Then, I was able to access the site
![](./9.png)

I stopped the container using the docker stop command and the site became inaccessible
![](./12.png)

I also restarted the container using docker start command
![](./13.png)

Then I tagged the image to match my docker hub repository
![](./14.png)

I then logged into the docker hub registry using my username and password
![](./16.png)

I then pushed my custom image to docker hub
![](./17.png)

And confirmed the push by logging into docker hub from my browser
![](./18.png)

![](./19b.png)

