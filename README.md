# Logging Bucket Setup
Create a bucket to store logs for a region

## Prerequisites
[AWS CLI](http://docs.aws.amazon.com/rekognition/latest/dg/setup-awscli.html)

## Setup
Run in the GitHub repo dir and add a --region argument if you need to run in a region that isn't the default.

```
aws cloudformation create-stack --stack-name rLoggingBucket --template-body file://./cfn-logging-bucket.yaml
```
