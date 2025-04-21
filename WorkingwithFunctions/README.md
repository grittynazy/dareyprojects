# WORKING WITH FUNCTIONS
Functions are used to organize code to maintain clarity and efficiency

This is a script without a function
#!/bin/bash

# Checking the number of arguments
if [ "$#" -ne 0 ]; then
    echo "Usage: $0 <environment>"
    exit 1
fi

# Accessing the first argument
ENVIRONMENT=$1

# Acting based on the argument value
if [ "$ENVIRONMENT" == "local" ]; then
  echo "Running script for Local Environment..."
elif [ "$ENVIRONMENT" == "testing" ]; then
  echo "Running script for Testing Environment..."
elif [ "$ENVIRONMENT" == "production" ]; then
  echo "Running script for Production Environment..."
else
  echo "Invalid environment specified. Please use 'local', 'testing', or 'production'."
  exit 2
fi

It would look like this with a function called check_num_of_args

#!/bin/bash

check_num_of_args() {"\n# Checking the number of arguments\nif [ \"$#\" -ne 0 ]; then\n    echo \"Usage: $0 <environment>\"\n    exit 1\nfi\n"}

# Accessing the first argument
ENVIRONMENT=$1

# Acting based on the argument value
if [ "$ENVIRONMENT" == "local" ]; then
  echo "Running script for Local Environment..."
elif [ "$ENVIRONMENT" == "testing" ]; then
  echo "Running script for Testing Environment..."
elif [ "$ENVIRONMENT" == "production" ]; then
  echo "Running script for Production Environment..."
else
  echo "Invalid environment specified. Please use 'local', 'testing', or 'production'."
  exit 2
fi

When a function is defined in a shell script, it remains inactive until it is invoked or called within athe script. To execute the script, a call must be placed to the function in a relevant part of the script

The script would now look like 

#!/bin/bash

# Checking the number of arguments
if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <environment>"
    exit 1
fi

ENVIRONMENT=$1

# Acting based on the argument value
if [ "$ENVIRONMENT" == "local" ]; then
  echo "Running script for Local Environment..."
elif [ "$ENVIRONMENT" == "testing" ]; then
  echo "Running script for Testing Environment..."
elif [ "$ENVIRONMENT" == "production" ]; then
  echo "Running script for Production Environment..."
else
  echo "Invalid environment specified. Please use 'local', 'testing', or 'production'."
  exit 2
fi


With a refactored version of the code, we now have the flow like this;
1. Environment variable moved to the top
2. Function defined
3. Function call
4. Activate based on infrastucture environment section

Modifying the above to encapsulate number 4 in a function and call all the functions at the end of the script. This would look like

#!/bin/bash

#!/bin/bash

# Get the environment variable from user input
ENVIRONMENT=$1

# Function to check the number of arguments
check_num_of_args() {
  if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <environment>"
    exit 1
  fi
}

# Function to activate based on environment
activate_infra_environment() {
  case "$ENVIRONMENT" in
    local)
      echo "[INFO] Running script for Local Environment..."
      ;;
    testing)
      echo "[INFO] Running script for Testing Environment..."
      ;;
    production)
      echo "[INFO] Running script for Production Environment..."
      ;;
    *)
      echo "[ERROR] Invalid environment specified. Use 'local', 'testing', or 'production'."
      exit 2
      ;;
  esac
}

# Function to check if AWS CLI is installed
check_aws_cli() {
  if ! command -v aws &> /dev/null; then
    echo "[ERROR] AWS CLI is not installed."
    echo "Install it by following: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html"
    exit 3
  else
    echo "[INFO] AWS CLI is installed."
  fi
}

The config file stores configuration settings for AWS services and clients. A profile will enable you to easily switch between different AWS configurations. Setting up an environment variable by running the command export AWS_PROFILE=testing will pick up the configuration from both file and authenticate you to the testing environment

This is what the function will look like
#!/bin/bash

# Function to check if AWS_PROFILE is set
check_aws_profile() {
  if [ -z "$AWS_PROFILE" ]; then
    echo "[ERROR] AWS_PROFILE is not set."
    echo "Run: export AWS_PROFILE=<your-profile-name>"
    exit 4
  else
    echo "[INFO] AWS profile is set to '$AWS_PROFILE'."
  fi
}

# Execution order
check_num_of_args "$@"
activate_infra_environment
check_aws_cli
check_aws_profile


Ensure you have the following profiles in ~/.aws/credentials and ~/.aws/config
[default]
aws_access_key_id = YOUR_ACCESS_KEY_ID
aws_secret_access_key = YOUR_SECRET_ACCESS_KEY

[profile testing]
aws_access_key_id = TESTING_ACCESS_KEY_ID
aws_secret_access_key = TESTING_SECRET_ACCESS_KEY

[profile production]
aws_access_key_id = PROD_ACCESS_KEY_ID
aws_secret_access_key = PROD_SECRET_ACCESS_KEY

