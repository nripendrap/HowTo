Serverless 101

1. Serverless
Enables you to build scalable applications quickly without managing any servers

2. Low Cost
Serverlss applications are event-driven and you are only charged when your code is executed.

3. AWS Handles the Heavy Lifting
You can focus on writing code and building your application instead of configuring servers.

Lambda Exam Tips

Extremely Cost Effective
Pay only when your code executes

Continuous Scaling
Lambda scales automatically

Event-Driven
Lambda functions are triggered by an event or action

Independent
Lambda functions are independent. Each event will trigger a single function.

Serverless Technology
Lambda, API Gateway, DynamoDB, S3, SNS, SQS

__AWS services that can invoke Lambda functions.__

Lambda Triggers
- DynamoDB
- Kinesis
- SQS
- Application Load Balancer
- API Gateway
- Alexa
- CloudFront
- S3
- SNS
- SES
- CloudFormation
- CloudWatch
- CodeCommit
- CodePipeline

API Gateway Exam Tips

API Gateway
An API is like the front door to your application.
API Gateway provides an endpoint to your application running in AWS.

Serverless
Low cost and scales automatically.

Throttling
You can throttle API application from being overloaded by too many requests.

CloudWatch
Everything is logged to CloudWatch
For example, API calls, latencies, and errors.


__Lambda Versions__

- $LATEST is always the last version of code you uploaded to Lambda
- Use Lambda Versioning and Aliases to point your applications to a specific version if you don't want to use $LATEST
    - arn:aws:lambda:eu-west-2:7384500006350:function:mylambda:Prod
    - arn:aws:lambda:eu-west-2:7384500006350:function:mylambda:$LATEST
- If your application uses an alias, instead of $LATEST  remember that it will not automatically use new code whn you upload it

__Lambda Concurrent Execution Limits__
- Know that a limit exists - 1,000 concurrent executions per second
- If you are running a serverless website like ACG, it's likely you will hit the limit at some point
- If you hit the limit you will start to set invocation being rejected - 429 HTTP status code
- The remedy is to get the limit raised by AWS support
- __Reserved concurrency__ guarentees a set number of concurrnt executions are always available to a critical function

__Lambda and VPCs__
- It is possible to enable Lambda to access resources which are inside a private VPC.
- Provide VPC config to the function - private subnet ID, security group ID.
- Lambda uses the VPC information to set up ENIs using an IP from the private subnet CIDR range.
- The security group then allows your function to access resources in VPC.

__Step Functions__
1. Visualize
Great way to visualize your serverless application.

2. Automate
Step Functions automatically trigger and track each step. The output of one step is often the input to the next.

3. Logging
Step Functions log the state of each step, so if something goes wrong you can track what went wrong, and where.

__X-Ray__
__Analyze and Debug__
X-Ray helps developers analyze and debug distributed applications.

__Service Map__
The Service Map is a visual representation of your application.

__X-Ray Agent And SDK__
The X-Ray agent must be installed on your EC2 instance. Use the SDK to instrument your application to send traces to X-Ray.

__X-Ray Configuration__
High-Level Configuration Steps
- X-Ray integrates with many AWS services like DynamoDB, Lambda, API Gateway, etc.
- You can also intrument your own applications to send data to X-Ray.
- Application can be running on EC2, Elastic Beanstalk environments, on-premises systems and ECS.
- For ECS, run the X-Ray deamon in it's own Docker image, running alongside your application.
- You'll need three things:
    1. X-Ray SDK.
    2. X-Ray daemon.
    3. Instrument your application using the SDK to send the required data to X-Ray, e.g. data about incoming HTTP requests to your application.
- If you want to also record application specific information in the form of key-value pairs, use __annotations__ to add user defined key-value pairs to your X-Ray data - allows you to filter, index and search within X-Ray, e.g. game_name=TicTacToe,game_id=2645445842

__API Gateway Caching__
1. Improves Performance
Improve the performances of your APIs by caching the output of API calls to avoid calling your backend every time.
2. TTL
Responses are cached for a TTL period. The default TTL is 300 seconds (5 mins).
3. Reduces the Number of API Calls
API Gateway returns the cached response instead of making a new request to your application.

__API Gateway Throttling__
Default limits: 10,000 rps and 5,000 concurrent requests.
If you exceed the limit, API Gateway will return an error:
429, Too Many Requests.

API Gateway uses throttling to prevent your API from being overwhelmed by too many requests.

__Advanced API Gateway__
You can import APIs using external definition files, e.g., OpenAPI, formerly know as Swagger.

When dealing with legacy application which use SOAP, you can configure API Gateway as a SOAP web service passthrough, or you can use API Gateway to convert the XML response to JSON.
