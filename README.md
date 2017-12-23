# Logging Bucket Setup
Create a bucket to store logs for a region

## Notes
If you delete the stack, the logging bucket sticks around. You must manuall delete the log files and the bucket if that is what you really want!

## Prerequisites
[AWS CLI](http://docs.aws.amazon.com/rekognition/latest/dg/setup-awscli.html)

## Setup
Run in the GitHub repo dir. This commands below use StackSets to deploy to all regions

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$Failure tolerance count is set to 1 since eu-west-3 does not support GuardDuty yet.

```
aws cloudformation create-stack-set --stack-set-name LoggingBuckets --template-body file://./cfn-logging-bucket.yaml --region us-east-1

TEMP_ACCOUNTID='TheAccountId'
TEMP_ALLREGIONS=$(aws ec2 describe-regions --query 'Regions[].{Name:RegionName}' --output text | paste -sd " " -)
aws cloudformation create-stack-instances --stack-set-name LoggingBuckets --accounts $TEMP_ACCOUNTID --regions $TEMP_ALLREGIONS --region us-east-1 --operation-preferences FailureToleranceCount=0