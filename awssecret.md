# Retrieving Secrets from AWS Secrets Manager

This guide will walk you through the process of retrieving secrets from AWS Secrets Manager using a shell script.

## Step 1: Install AWS CLI

First, you need to install the AWS CLI. You can download it from the official AWS website. Once downloaded, you can install it using the following command:

```bash
# "Installing AWS CLI..."
pip install awscli --upgrade --user
```

## Step 2: Configure AWS CLI

Before you can retrieve secrets from AWS Secrets Manager, you need to configure your AWS CLI. Open your terminal and type the following command:

```bash
# "Configuring AWS CLI..."
aws configure
```

You will be prompted to provide the following:

You will obtain the following credentials from the IAM (Identity and Access Management) service in AWS. These credentials are generated when you create a new IAM user. Ensure that the IAM user has the necessary role permissions to access AWS Secrets Manager.

- `AWS Access Key ID`: Enter your AWS Access Key ID here.
- `AWS Secret Access Key`: Enter your AWS Secret Access Key here.
- `Default region name`: Enter your default AWS region here (e.g., us-west-2).
- `Default output format`: Enter your preferred output format (e.g., json).

## Step 3: Retrieve the Secret

Once your AWS CLI is configured, you can retrieve the secret from AWS Secrets Manager. You need to know the name of your secret (referred to as `secret-name` in the command below). You can find this in the AWS Secrets Manager console on the AWS website.

```bash
# "Retrieving secret..."
aws secretsmanager get-secret-value --secret-id secret-name
```

## Step 4: Save Secret to .env File

After retrieving the secret from AWS Secrets Manager, you can save it to a `.env` file. This can be done using the following command:

```bash
# "Saving secret to .env file..."
aws secretsmanager get-secret-value --secret-id secret-name --query SecretString --output text > .env
```

This command will write the secret value to a `.env` file in the current directory. The `--query SecretString --output text` part of the command extracts the secret value from the AWS CLI response and outputs it as plain text.

Please replace `secret-name` with the name of your secret. Also, ensure that your `.env` file is added to your `.gitignore` file to prevent it from being committed to your version control system.

This will output the secret value to your terminal. The `get-secret-value` is a command provided by AWS CLI to retrieve the value of a secret. The `--secret-id` is a parameter where you specify the name or ARN of the secret you want to retrieve.
