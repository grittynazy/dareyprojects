# AWS - Creating Resources with Functions and Introducing Arrays
For this project, I created a script with 2 functions, one for provisioning EC2 instances and another for setting up S3 buckets

## Function to provision EC2 instances

#!/bin/bash

# Function to create EC2 instances
create_ec2_instances() {
    # Specify the parameters for the EC2 instances
    instance_type="t2.micro"
    ami_id="ami-0cd59ecaf368e5ccf"  
    count=2  # Number of instances to create
    region="eu-west-2" # Region to create cloud resources
    key_name="MyKeyPair"

    echo "[INFO] Creating $count EC2 instance(s) in $region..."

    # Create the EC2 instances
    aws ec2 run-instances \
        --image-id "$ami_id" \
        --instance-type "$instance_type" \
        --count "$count" \
        --key-name "$key_name" \
        --region "$region"

    # Check if the EC2 instances were created successfully
    if [ $? -eq 0 ]; then
        echo "[SUCCESS] EC2 instances created successfully."
    else
        echo "[ERROR] Failed to create EC2 instances."
    fi
}

# Call the function to create EC2 instances
create_ec2_instances

## Purpose of the Script
This Bash script automates the creation of two EC2 instances in AWS using the AWS CLI. It’s useful for quickly launching virtual machines without manually going through the AWS Console.

### Step-by-Step Breakdown
#### Function Definition
The script defines a function called create_ec2_instances to group the EC2 creation logic. Functions help modularize the script and allow reusability.

#### Parameter Setup Inside the Function
These are the required inputs for launching EC2 instances:

instance_type="t2.micro": Specifies the instance size (small and within free tier).

ami_id="ami-0cd59ecaf368e5ccf": Amazon Machine Image ID — this is the OS image the instance will use.

count=2: Number of EC2 instances to create.

region="eu-west-2": The AWS region where the instances will be launched (London).

key_name="MyKeyPair": The name of an existing key pair in that region (used for SSH access).

#### Instance Creation with AWS CLI
The aws ec2 run-instances command uses the above parameters to launch the instances. The \ at the end of each line is used to break the command into multiple lines for better readability.

Error Handling

$? checks the exit status of the last command (aws ec2 run-instances).

If the command was successful (0), it prints a success message.

If it failed (non-zero), it prints an error message.

#### Function Execution
After defining the function, the script calls create_ec2_instances to run the actual EC2 creation process.

### Requirements to Run This Script
AWS CLI must be installed and configured with appropriate credentials.

The specified AMI ID and key pair must exist in the chosen region.

## Bash Script to Create S3 bucket for different departments

#!/bin/bash

# Function to create S3 buckets for different departments
create_s3_buckets() {
    # Define a company name as prefix
    company="datawise"

    # Array of department names
    departments=("Marketing" "Sales" "HR" "Operations" "Media")

    # Loop through the array and create S3 buckets for each department
    for department in "${departments[@]}"; do
        bucket_name="${company}-${department}-data-bucket"
        
        # Create S3 bucket using AWS CLI
        aws s3api create-bucket \
            --bucket "$bucket_name" \
            --region your-region \
            --create-bucket-configuration LocationConstraint=your-region

        if [ $? -eq 0 ]; then
            echo "✅ S3 bucket '$bucket_name' created successfully."
        else
            echo "❌ Failed to create S3 bucket '$bucket_name'."
        fi
    done
}

# Call the function to create S3 buckets
create_s3_buckets

### Purpose of the Script:
This Bash script automates the creation of Amazon S3 buckets for different departments in a company. It uses the AWS CLI and follows best practices like using a naming prefix and validating results.

### Script Breakdown:
create_s3_buckets() {
This defines a function called create_s3_buckets. Functions let you group related code into reusable blocks.

company="datawise"
This sets a variable company that will be used as a prefix for all bucket names to maintain naming consistency.

departments=("Marketing" "Sales" "HR" "Operations" "Media")
This is an array of department names. We’ll loop through this list to create a bucket for each department.

for department in "${departments[@]}"; do
This starts a for loop that will run once for each department in the array.

"${departments[@]}" expands the array into individual elements.

bucket_name="${company}-${department}-data-bucket"
Constructs the bucket name by combining the company name, department, and a suffix. Example: datawise-HR-data-bucket.

aws s3api create-bucket \
    --bucket "$bucket_name" \
    --region your-region \
    --create-bucket-configuration LocationConstraint=your-region
This command creates the S3 bucket using AWS CLI.

--bucket specifies the name.

--region and LocationConstraint set the AWS region (replace your-region with something like eu-west-2).

### LocationConstraint is needed for all regions except us-east-1.

if [ $? -eq 0 ]; then
$? stores the exit code of the last command.

0 means success. If the bucket was created successfully, this block runs:

echo "✅ S3 bucket '$bucket_name' created successfully."
else
    echo "❌ Failed to create S3 bucket '$bucket_name'."
If the bucket creation failed, this block runs instead.

done
Closes the for loop.

create_s3_buckets
This calls the function so that the S3 buckets are actually created when the script is run.

## A more comprehensive script that combines the 2 functions 
#!/bin/bash

# Accept environment name as first argument
ENVIRONMENT=$1

# Check if the correct number of arguments is passed
check_num_of_args() {
  if [ $# -ne 1 ]; then
    echo "Usage: $0 <environment>"
    echo "Valid environments: local, testing, production"
    exit 1
  fi
}

# Activate infrastructure based on the environment
activate_infra_environment() {
  case "$ENVIRONMENT" in
    local)
      echo "Running script for Local Environment..."
      ;;
    testing)
      echo "Running script for Testing Environment..."
      ;;
    production)
      echo "Running script for Production Environment..."
      ;;
    *)
      echo "Invalid environment: $ENVIRONMENT"
      echo "Valid environments: local, testing, production"
      exit 2
      ;;
  esac
}

# Check if AWS CLI is installed
check_aws_cli() {
  if ! command -v aws &> /dev/null; then
    echo "AWS CLI is not installed. Please install it before proceeding."
    exit 3
  fi
}

# Check if AWS profile is set
check_aws_profile() {
  if [ -z "$AWS_PROFILE" ]; then
    echo "AWS_PROFILE environment variable is not set."
    exit 4
  fi
}

# Create EC2 instances
create_ec2_instances() {
  echo "Creating EC2 instances..."
  instance_type="t2.micro"
  ami_id="ami-0cd59ecaf368e5ccf"  # Replace with a valid AMI for your region
  count=2
  region="eu-west-2"

  aws ec2 run-instances \
    --image-id "$ami_id" \
    --instance-type "$instance_type" \
    --count "$count" \
    --key-name "MyKeyPair" \
    --region "$region"

  if [ $? -eq 0 ]; then
    echo "✅ EC2 instances created successfully."
  else
    echo "❌ Failed to create EC2 instances."
  fi
}

# Create S3 buckets for different departments
create_s3_buckets() {
  echo "Creating S3 buckets..."
  company="datawise"
  region="eu-west-2"
  departments=("Marketing" "Sales" "HR" "Operations" "Media")

  for department in "${departments[@]}"; do
    bucket_name="${company}-${department,,}-data-bucket"  # Lowercase with ,,
    
    aws s3api create-bucket \
      --bucket "$bucket_name" \
      --region "$region" \
      --create-bucket-configuration LocationConstraint="$region"

    if [ $? -eq 0 ]; then
      echo "✅ S3 bucket '$bucket_name' created."
    else
      echo "❌ Failed to create S3 bucket '$bucket_name'."
    fi
  done
}

# ---------------------------
# Main Script Execution
# ---------------------------

check_num_of_args "$@"
activate_infra_environment
check_aws_cli
check_aws_profile
create_ec2_instances
create_s3_buckets
