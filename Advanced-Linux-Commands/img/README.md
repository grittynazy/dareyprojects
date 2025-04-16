## LINUX ADVANCED COMMANDS
I utilised more complex linux commands and learnt how to use them to grant file permissions, create users, groups and give them ownership of a file or directory

I created a file
![](./touch%20script.png)

I checked the permissions of the file
![](./ls%20-latr%20script.png)

I updated the permissions to grant execute permissions to the file
![](./chmod%20+x,%20-ls.png)

I also used the number format to grant permissions
![](./chmod%20755.png)

I allowed group members to read, write and execute the file
![](./chmod%20777.png)

I used the chown command to grant permission to another user and group
![](./chown.png)

I switched to the root user using sudo and exited
![](./sudo%20-i.png)

I created a user, and her home directory was automatically generated for her and I assigned her to the sudo group
![](./adduser%20johndoe.png)
![](./usermod.png)

I switched to another user's account
![](./su.png)

I changed the password of a user
![](./sudo%20passwd.png)

I created a group
![](./groupadd.png)

I added users to the created group
![](./usermod%20developers.png)

I verified the group membership of the user
![](./id.png)

I deleted a user
![](./userdel.png)

I created a group and named it devops
![](./groupadd%20devops.png)

I created some users and ensured each user belongs to the devops group
![](./useradd%204users.png)
![](./useradd%20Mary.png)

I created a folder for a user in the /home directory and ensured group ownership of the created folder belongs to devops
![](./chown%20final.png)

I also gave others write permissions
![](./chmod%20o+w.png)