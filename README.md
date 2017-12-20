# Logging Bucket Setup Scripts
Create a bucket to store logs for a region

## Prerequisites
[AWS CLI](http://docs.aws.amazon.com/rekognition/latest/dg/setup-awscli.html)

## Setup
```
aws cloudformation create-stack --stack-name rLoggingBucket --template-body file://./cfn-logging-bucket.yaml
```
