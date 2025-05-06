# AWS S3 MINI PROJECT
The goal of this project was to familiarize myself with S3 bucket and it's fundamental concept such as

Firstly, I created an S3 bucket
![](./1%20main.png)
I made sure public access to the bucket was blocked
![](./2.png)
I disabled versioning
![](./3.png)

## Uploading file to S3 bucket
I uploaded a file to the S3 bucket
![](./4.png)
I then editted the properties of the bucket and enabled versioning
![](./5.png)
I added another line of text to the initial file and uploaded it to create another version
![](./6.png)
![](./7.png)

I also enabled public access to the bucket and edited the bucket policy to allow the Getobject and Getobject version statements
![](./8.png)
I then clicked on the object url and was able to view the 2 versions of the file
![](./9.png)
![](./10.png)
I set a lifecycle policy to transition objects to standard infrequent access after 30days
![](./11.png)
![](./12main.png)