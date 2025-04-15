# BASIC LINUX COMMANDS
I will be documenting some basic linux commands and how they are used in the terminal

## Sudo Command
I tried creating a folder in /root directory. This caused a permission denied error
![](./mkdir%20root.png)

I used sudo to successfully create the folder
![](./sudo%20mkdir%20root.png)

I verified the folder's creation using the ls command
![](./sudo%20ls%20root.png)

I listed the files and directories in the root file system
![](./ls%20-l.png)

I used the cd command to navigate to one of the directories in the output above
![](./cd-pwd-usr.png)

## pwd
I used the pwd command to find the path of my current working directory
![](./pwd.png)

I created a folder in /usr 
![](./mkdir%20photos-ls.png)

I created 3 more random directories inside the photos directory
![](./mkdir%20png-jpg-zip.png)

I utilized the ls command to list the content of the directory
![](./ls%20png-jpg-zip.png)

## cat command
I used the cat command to list the content of a file
![](./cat%20etc-os-release.png)

## cp command
I used the cp command to copy the content of a file into a directory
![](./cp%20file.jpg%20home-ubuntu-docs.png)

..to copy multiple files into a directory
![](./cp%20file1,2,3.png)

..to copy one file into another file
![](./cp%20file-file1.png)

..and to copy an entire directory into a destination directory
![](./cp%20-R.png)

## mv command
This can be used to move a file from one directory to another
![](./mv%20file3%20home-ubuntu...png)

..or rename a file
![](./mv%20file%20file5.png)

## rm command
I used the rm command to delete a single file as well as multiple files
![](./rm%20file1,2,3.png)

## touch command
I used the touch command to create a file
![](./touch.png)

## find command
I used the find command to search for files within a directory
![](./find.png)