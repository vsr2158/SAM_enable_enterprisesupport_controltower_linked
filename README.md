# Enable Enterprise Support on AWS Control Tower Linked Account 

Using multi account strategy to manage your AWS environment is recommended best practice. One way to manage and govern multi account is to use [AWS Control Tower](https://aws.amazon.com/controltower/).

As part of operational activity all AWS accounts needs to be enrolled into the right [support level](https://aws.amazon.com/premiumsupport/plans/). AWS Control Tower makes account creation with required security and gobernance controls easy, and provides you options to do further customizations using [lifecycle events](https://docs.aws.amazon.com/controltower/latest/userguide/lifecycle-events.html).

This project utilizes once such event "CreateManagedAccount" to automate support case creation requesting the newly created account to be enrolled in Enterprise Support tier. 

AWS Serverless Application Model is a great way to package and quickly deploy serverless applications such of these which are completely event driven, to learn more about SAM refer to [AWS documentation](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html).

This project contains source code and supporting files for a serverless application that you can deploy with the SAM CLI. It includes the following files and folders:

- functions - Code for the application's Lambda functions to check the value of, buy, or sell shares of a stock.
- template.yaml - A template that defines the application's AWS resources.

### Architecture
![](https://github.com/vsr2158/SAM_enable_enterprisesupport_controltower_linked/blob/master/enable_es.drawio.png?raw=1)

## Deploy

The Serverless Application Model Command Line Interface (SAM CLI) is an extension of the AWS CLI that adds functionality for building and testing Lambda applications. It uses Docker to run your functions in an Amazon Linux environment that matches Lambda.

To use the SAM CLI, you need the following tools:

* SAM CLI - [Install the SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)
* [Python 3 installed](https://www.python.org/downloads/)

To build and deploy your application for the first time, run the following in your shell:

```bash
sam build 
sam deploy --guided
```

The first command will build the source of your application. The second command will package and deploy your application to AWS, with a series of prompts:

* **Stack Name**: The name of the stack to deploy to CloudFormation. This should be unique to your account and region, and a good starting point would be something matching your project name.
* **AWS Region**: The AWS region you want to deploy your app to.
* **Confirm changes before deploy**: If set to yes, any change sets will be shown to you before execution for manual review. If set to no, the AWS SAM CLI will automatically deploy application changes.
* **Allow SAM CLI IAM role creation**: Many AWS SAM templates, including this example, create AWS IAM roles required for the AWS Lambda function(s) included to access AWS services. By default, these are scoped down to minimum required permissions. To deploy an AWS CloudFormation stack which creates or modifies IAM roles, the `CAPABILITY_IAM` value for `capabilities` must be provided. If permission isn't provided through this prompt, to deploy this example you must explicitly pass `--capabilities CAPABILITY_IAM` to the `sam deploy` command.
* **Save arguments to samconfig.toml**: If set to yes, your choices will be saved to a configuration file inside the project, so that in the future you can just re-run `sam deploy` without parameters to deploy changes to your application.

## Cleanup

To delete the sample application that you created, use the AWS CLI. Assuming you used your project name for the stack name, you can run the following:

```bash
aws cloudformation delete-stack --stack-name function_enable_enterprisesupport_controltower_linked
```

## Resources

See the [AWS SAM developer guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) for an introduction to SAM specification, the SAM CLI, and serverless application concepts.

Next, you can use AWS Serverless Application Repository to deploy ready to use Apps that go beyond hello world samples and learn how authors developed their applications: [AWS Serverless Application Repository main page](https://aws.amazon.com/serverless/serverlessrepo/)
