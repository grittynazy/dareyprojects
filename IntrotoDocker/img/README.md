# Introduction to Docker
In this project, I got started by installing docker. Firstly, I refreshed the package list ensuring the latest software is available for installation.
![](./1.png)

Then I installed essential packages, including certificate authorities, a data transfer tool (curl), and the GNU Privacy Guard for secure communication and package verification.
![](./2.png)

I created a directory which is used for docker's authentication,downloaded the docker GPG key and set read permissions for all users on the docker GPG key file within the APT keyring directory. I then used the echo command to create a docker APT repository configuration entry for the ubuntu system and wrote this configuration to the docker.list file
![](./3.png)


I then installed the latest version of docker 
![](./4.png)

I verified that docker has been successfully installed
![](./5.png)

I used the docker run command to execute a "Hello World" container
![](./6.png)

I checked if the images are present in my local machine
![](./7.png)

The docker ps command shows the containers running while the docker ps -a command shows all containers whether running or stopped
![](./8.png)

![](./9.png)

docker stop commands stops a running container while the docker rm command deletes a container and docker rmi command deletes an image
![](./10.png)

![](./11.png)