# Setting Up Minikube

Minikube is an open source tool that enables the running of Kubernestes clusters on locally on machines

### Installing minikube on Linux

I set up a linux server on AWS with 20gb disk storage, 2vcpu and 4gn RAM
![](./1.png)
![](./2.png)


This is a linux command that refreshes the package list on a Debian-based system ensuring the latest software information is available for installation. 
![](./3.png)

This is a linux command that installs essential packages including certificate authorities, curl and GNU Privacy Guard for secure communication and package verification
![](./4.png)

These commands create a directory with specific permissions for storing keyring files, which are used for docker's authentication, download the Docker GPG key using curl, sets read permissions for all users on the Docker GPG key file within the APT key ring directory and adds the repository to APT sources

![](./5.png)

The following commands install latest version of docker and verifies that docker has been successfully installed
![](./6.png)

![](./7.png)

The following commands downloads minikube's binary and installs minikube using dpkg
![](./8.png)

The following commands start minikube and downloads kubectl to interact with the kubernetes cluster

![](./11.png)
![](./12.png)

![](./10.png)

I tried to interact with cluster using kubectl
![](./13.png)

I ran the minikube dashboard command. The minikube dashboard is a command that opens a web-based Kubernetes dashboard for a local Kubernetes cluster running via Minikube.

![](./14.png)

![](./16.png)

## Working With Kubernetes Nodes
I ran minikube start and it completed successfully. This implies I have just launched a single-node Kubernetes cluster locally. I then verified the cluster is running
![](./17.png)

![](./18.png)

I then created a simple kubernetes deployment, exposed it and viewed it in my browser
![](./19.png)

![](./20.png)

![](./21.png)

![](./22.png)

I checked the logs to verify that everything was working fine
![](./23.png)

I then scaled the deployment to 3 replicas and confirmed that the number of pods had increased to 3
![](./24.png)

I then stopped the running minikube preserving the cluster state and deleted the minikube kubernetes cluster and its associated resources
![](./25.png)