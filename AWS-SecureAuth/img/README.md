# Setting Up Secure Authentication to AWS API
This set up involves establishing an IAM role and then designing an IAM policy granting full access to both EC2 and S3. Then an IAM user is created and assigned the role and the permission defined in the IAM policy. Then access key id and secret key was generated for the user.

## Installing and Configuring AWS CLI
AWS CLI is a powerful tool that allows intersction with AWS services directly from the terminal, enabling automation and simplification of AWS resource management

## Configuring the AWS CLI
This command is used to configure the CLI
aws configure
Then, when prompted, the access key and secret aceess key, default region and default output format are inputted

To confirm that the CLI was configured properly, run 
aws ec2 describe-regions --output table
This command queries the EC2 service for a list of all regions and formats the output as a table