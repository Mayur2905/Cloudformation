# CloudFormation Template Documentation

## Overview
This CloudFormation template creates an Amazon Simple Notification Service (SNS) topic and subscribes an email endpoint to it.

## Resources
- **SNS Topic**: Creates an SNS topic with the display name `MySNSTopic` and the topic name `my-sns-topic`.
- **SNS Subscription**: Subscribes an email endpoint (`mayurgaikwad0101@gmail.com`) to the SNS topic.

## Parameters
This template does not use any parameters.

## Outputs
This template does not have any outputs.

## Usage Instructions
1. Open the AWS Management Console and navigate to CloudFormation.
2. Click "Create stack" and choose to upload the template file.
3. Follow the wizard to create the stack. The SNS topic and subscription will be created automatically.
