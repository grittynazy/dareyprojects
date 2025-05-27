# Working With Docker Containers

Docker containers are lightweight, portable, and executable units that encapsulate an app and its dependencies.

### Running Containers
I started by first pulling the image
![](./12.png)

To run a container, I used the docker run command followed by the name of the image
![](./1.png)

The image below show that the container was created but not running
![](./2.png)

I started the container by running docker start container_id
![](./3.png)

I ran a command that prints all available system information in one line. It gives you a comprehensive overview of the system’s kernel and operating system.

![](./13.png)
### Launching containers with different options

Here, I ran a container with a specific environment variable
![](./4.png)

### Running containers in the background
I also ran a container in the background, using the -d option
![](./5.png)

### Container Lifecycle
Containers have a lifecycle that includes creating, starting, stopping, and restarting. 

Here, I started the container using the image name and got an error message
![](./6.png)
I then started the container using the container name and it worked
![](./7.png)

This is the evidence of the running container
![](./14.png)

I stopped the container
![](./8.png)

And confirmed by running the docker ps -a command
![](./15.png)

And also restarted the container
![](./9.png)

![](./16.png)

Finally, I removed the container and confirmed it by running the docker ps -a command
![](./10.png)

![](./11.png)