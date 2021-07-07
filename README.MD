# EC2 Instance Scheduler

Schedule the start and stop of an Amazon EC2 instance using Lambda functions and CloudWatch event rules.

## Lambda
Create the following lambda functions. These will be called by CloudWatch rules at scheduled times.
- startEC2Instance
- stopEC2Instance

## CloudWatch
Create two CloudWatch rules (start and stop) that pass the instanceRegion, instanceId to the Lambda functions.

### CloudWatch Input - Constant (JSON text)
> { "instanceRegion": "us-east-1", "instanceId": "i-1234567890abcdef0" }

- Starting the EC2 instance
    - Schedule a rule with the desired start time as a Cron expression
    - Invoke lambda function: startEC2Instance
    - Configure input as Constant (JSON text)
- Stopping the EC2 instance
    - Schedule a rule with the desired stop time as a Cron expression
    - Invoke lambda function: stopEC2Instance
    - Configure input as Constant (JSON text)
