# INTRODUCTION TO CLOUD COMPUTING - SECURITY AND IDENTITY AND ACCESS MANAGEMENT

I logged into the AWS Management console using my root user credentials, created policies for 2 groups, and added users to the groups

## Create policy for the Development team

![](./create-policy.png)

![](./policy-details1.png)

![](./developers-policy.png)

## Create policy for the Analyst team
![](./create-s3-policy.png)

![](./policy-details2.png)

![](./analyst-policy.png)

## Create a User group for the Development Team
![](./create-group-devt.png)

Attach policies to the Development Team
![](./attach-policy-to-devt-group.png)

![](./devt-team-created.png)

## Create a User group for the Analyst Team
![](./create-group-analyst.png)

Attach policies to the Analyst Team
![](./create-group-analyst-2.png)

![](./analyst-group-created.png)

## Create User John
![](./create-user-john.png)

Add John to Development Team Group group
![](./add-userto-group.png)

![](./review%20and%20create%20user%20john.png)

![](./user-john-created.png)

## Create User Mary
![](./create-user-mary.png)

Add Mary to Analyst Team Group
![](./add-usermary-togroup.png)

![](./review-and-create-user-mary.png)
![](./user-mary-created.png)

## Sign in as John
![](./john-signin.png)
![](./password-change.png)

Permission denied for John to create S3 bucket 
![](./correction.png)

John granted permission to launch Ec2 instance
![](./john-instance.png)

## Sign in as Mary
![](./mary-sign-in.png)

Permission denied for Mary to create an launch an EC2 instance
![](./perm-denied-mary.png)

Mary is able to create an S3 bucket
![](./mary-bucket-success.png)

## Enabling MFA
For John
![](./john-enabled-without-mfa-main.png)
![](./john-mfa-device-setup.png)
![](./authenticator-app-confirm.png)
![](./john-with-mfa.png)

For Mary
![](./mary-without-mfa.png)
![](./add-auth-app-for%20mary.png)
![](./authenticator-app-confirm.png)




