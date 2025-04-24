# E-COMMERCE PLATFORM DEPLOYMENT WITH GIT, LINUX AND AWS
 In order to achieve this deployment, I started with the initializing of git
 ![](./mkdir-git%20init.png)

 I downloaded a website template and extracted the downloaded template into my project folder

 ![](./scp.png)

 ![](./ls.png)

 ![](./unzip.png)

![](./ls-unzip.png)

 ![](./cd-unzip-ls.png)
 
 I added the website files to my git repo, set the git global configuration with my username and password and committed the changes
 ![](./git%20add-config-commit.png)

 I created a remote repository on Github and linked my local repository to the remote
 ![](./git%20rep.png)
 ![](./git%20remote%20add%20origin.png)

 I then pushed the changes to Github
 ![](./git%20branch-push.png)

 ## AWS DEPLOYMENT
 To deploy the website, I started with setting up an EC2 instance. I logged into the AWS Management console, launched an EC2 instance using an Amazon Linux AMI and connected to the instance via SSH
 ![](./new-launch-ec2.png)

I cloned the Github repo to my EC2 instance using the 2 primary methods: SSH and HTTPS.

### SSH
On my EC2 instance, I generated SSH keypair using ssh-keygen
![](./new-ssh-keygen.png)

I displayed and copied my public key
![](./new-cat-publickey.png)

I added the public key to my Git hub account
![](./new-add-ssh-key.png)

 I navigated to my Github repo and selected code and then SSH and copied the link
![](./new-repo-ssh.png)

I used the SSH clone URL to clone the repository
![](./new-git%20clone-ssh.png)

### HTTPS
I navigated to my Github repo and selected code and copied the HTTPS link. I used this to clone the repo also
![](./new-git%20clone-https.png)

## Install a Web Server on EC2
I installed Apache web server on the EC2 instance
![](./new-install%20httpd.png)

I then cleared the default httpd web directory and copied my website files to it
![](./new-rm-cp.png)

I applied the changes by reloading the httpd service
![](./new-systemctl-reload.png)

I opened a web browser and accessed the public ip of my EC2 instance to view the deployed website
![](./new-website.png)

## Development New Features and Fixes

I created a development branch to isolate new features
![](./new-create-new-branch.png)

![](./new-devt%20branch.png)

![](./new-git-merge.png)

I staged my changes, committed pulled and pushed.
![](./new-git%20pull.png)
![](./new-git%20push%20main.png)
