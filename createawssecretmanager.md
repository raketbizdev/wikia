# Creating a New Secret in AWS Secrets Manager

This guide will walk you through the process of creating a new secret in AWS Secrets Manager.

## Step 1: Open AWS Secrets Manager

First, navigate to the AWS Management Console and open the AWS Secrets Manager service. You can find this by typing "Secrets Manager" into the search bar at the top of the page.

## Step 2: Start the Create Secret Wizard

Click on the "Store a new secret" button to start the Create Secret wizard.

## Step 3: Choose Secret Type

You will be prompted to choose the type of secret you want to store. This could be credentials for a database or other service, an API key, or just a freeform text secret. Choose the option that best suits your needs.

## Step 4: Input Secret Details

Next, you will be asked to input the details of your secret. If you chose to store credentials, you will need to input a username and password. If you chose to store an API key, you will need to input the key. If you chose to store freeform text, you can input any text you want.

## Step 5: Name and Describe Your Secret

You will then be asked to give your secret a name and an optional description. The name will be used to retrieve the secret later, so make sure it's something you can remember.

## Step 6: Configure Secret Rotation

Next, you can choose to enable automatic secret rotation. This is an optional step, but it can enhance the security of your secret by automatically changing it at regular intervals.

## Step 7: Review and Create Your Secret

Finally, review the details of your secret and click the "Store" button to create it. Your secret is now stored in AWS Secrets Manager and can be retrieved at any time.

Remember to keep your secret name handy, as you will need it to retrieve your secret using AWS CLI or SDKs.
