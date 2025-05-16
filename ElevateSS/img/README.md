# Elevate your SHell Scripting Journey
In this project, the objective was to develop a script that automates the setup of EC2 instances and S3 buckets. The script incorporates functions to modularize tasks like creatng Ec2 instances, configuring s3 buckets and verifying deployment statuses. The script uses arrays to manage a list of resources created, leverage environment variables to store sensitive information like AWS credentials, region settings and configuration parameters. The script accepts command line arguments and implements robust error handling mechanisms to catch and respond aws service disruptions.

This is the script below

#!/bin/bash

# ========= Global Config ===========
AWS_REGION="${AWS_REGION:-us-east-1}"
EC2_INSTANCE_TYPE="${EC2_INSTANCE_TYPE:-t2.micro}"

# Arrays to track resources
declare -a EC2_INSTANCE_IDS
declare -a S3_BUCKET_NAMES

# ======== Functions ==========

function error_exit() {
    echo "[ERROR] $1"
    exit 1
}

function create_ec2_instance() {
    local name="$1"
    echo "[INFO] Creating EC2 instance: $name"
    instance_id=$(aws ec2 run-instances \
        --image-id ami-0c02fb55956c7d316 \
        --instance-type "$EC2_INSTANCE_TYPE" \
        --region "$AWS_REGION" \
        --tag-specifications "ResourceType=instance,Tags=[{Key=Name,Value=$name}]" \
        --query "Instances[0].InstanceId" \
        --output text) || error_exit "Failed to create EC2 instance."
    
    EC2_INSTANCE_IDS+=("$instance_id")
    echo "[SUCCESS] EC2 Instance created: $instance_id"
}

function create_s3_bucket() {
    local bucket_name="$1"
    echo "[INFO] Creating S3 bucket: $bucket_name"
    aws s3api create-bucket \
        --bucket "$bucket_name" \
        --region "$AWS_REGION" \
        --create-bucket-configuration LocationConstraint="$AWS_REGION" \
        || error_exit "Failed to create S3 bucket."
    
    S3_BUCKET_NAMES+=("$bucket_name")
    echo "[SUCCESS] S3 Bucket created: $bucket_name"
}

function verify_resources() {
    echo "[INFO] Verifying created resources..."
    echo "EC2 Instances:"
    for id in "${EC2_INSTANCE_IDS[@]}"; do
        state=$(aws ec2 describe-instances --instance-ids "$id" --region "$AWS_REGION" --query "Reservations[].Instances[].State.Name" --output text)
        echo "  - $id: $state"
    done

    echo "S3 Buckets:"
    for bucket in "${S3_BUCKET_NAMES[@]}"; do
        aws s3api head-bucket --bucket "$bucket" --region "$AWS_REGION" &> /dev/null && echo "  - $bucket: Exists" || echo "  - $bucket: Not found"
    done
}

function usage() {
    echo "Usage: $0 --ec2-name <name> --s3-bucket <bucket-name>"
    exit 1
}

# =========== Argument Parsing ==========
while [[ "$#" -gt 0 ]]; do
    case $1 in
        --ec2-name) EC2_NAME="$2"; shift ;;
        --s3-bucket) S3_BUCKET_NAME="$2"; shift ;;
        *) echo "[ERROR] Unknown parameter passed: $1"; usage ;;
    esac
    shift
done

if [[ -z "$EC2_NAME" ]] || [[ -z "$S3_BUCKET_NAME" ]]; then
    usage
fi

# ========= Execution ==========
echo "[INFO] Starting automation script..."

create_ec2_instance "$EC2_NAME"
create_s3_bucket "$S3_BUCKET_NAME"
verify_resources

echo "[INFO] Automation script completed successfully."

