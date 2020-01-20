# Serverless Deploy And Run

In this module we'll breakdown the Wild Rydes application into three separate microservices.

Both microservices and monolith are valid serverless architecture choices. We use a microservices architecture here because it reduces the complexity of a single service and its configuration is easier to understand.

## Goals and Objectives:

**Objectives:**
* Understand constructing a serverless application with microservices

**Goals:**
* Deploy separate microservices to create Wild Rydes.

## Tech Stack

The Wild Rydes application has been broken down into two separate services. They are:

* [wild-rydes](https://github.com/ServerlessOpsIO/wild-rydes) - frontend website and ride request service.
* [wild-rydes-ride-fleet](https://github.com/ServerlessOpsIO/wild-rydes-ride-fleet) - Manages the available ride fleet.

![Wild Rydes Microservices](../../images/wild-rydes-arch.png)

## Instructions

### 1. Deploy wild-rydes-ride-fleet

Deploy the _wild-rydes-ride-fleet_ service. This service is a RESTful API that fetches available unicorns and returns their info to the requesting service. The service is composed of API Gateway, an AWS Lambda function, and a DynamoDB table.

Clone the GitHub repository, change into the directory, use NodeJS's _npm_ to install Serverless Framework plugins and deploy.

```
$ cd $WORKSHOP
$ git clone https://github.com/ServerlessOpsIO/wild-rydes-ride-fleet.git
$ cd wild-rydes-ride-fleet
$ npm install
$ sls deploy -v
```
<details>
<summary><strong>Output</strong></summary>
<p>

```
$ cd $WORKSHOP

$ git clone https://github.com/ServerlessOpsIO/wild-rydes-ride-fleet.git
Cloning into 'wild-rydes-ride-fleet'...
remote: Counting objects: 30, done.
remote: Total 30 (delta 0), reused 0 (delta 0), pack-reused 30
Unpacking objects: 100% (30/30), done.

$ cd wild-rydes-ride-fleet

$ npm install
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN wild-rydes-ride-fleet@0.1.0 No repository field.
npm WARN wild-rydes-ride-fleet@0.1.0 No license field.

added 62 packages in 6.523s

$ sls deploy -v
Serverless: Installing required Python packages with python3.6...
Serverless: Linking required Python packages...
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Unlinking required Python packages...
Serverless: Creating Stack...
Serverless: Checking Stack create progress...
CloudFormation - CREATE_IN_PROGRESS - AWS::CloudFormation::Stack - wild-rydes-ride-fleet-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_COMPLETE - AWS::CloudFormation::Stack - wild-rydes-ride-fleet-dev
Serverless: Stack create finished...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service .zip file to S3 (689.43 KB)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - wild-rydes-ride-fleet-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::RestApi - ApiGatewayRestApi
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - RequestUnicornLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::DynamoDB::Table - UnicornsTable
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - LoadTableLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::RestApi - ApiGatewayRestApi
CloudFormation - CREATE_IN_PROGRESS - AWS::DynamoDB::Table - UnicornsTable
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - RequestUnicornLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - LoadTableLogGroup
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::RestApi - ApiGatewayRestApi
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - RequestUnicornLogGroup
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - LoadTableLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Resource - ApiGatewayResourceUnicorn
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Resource - ApiGatewayResourceUnicorn
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Resource - ApiGatewayResourceUnicorn
CloudFormation - CREATE_COMPLETE - AWS::DynamoDB::Table - UnicornsTable
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_COMPLETE - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - RequestUnicornLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - LoadTableLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - RequestUnicornLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - LoadTableLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - RequestUnicornLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - LoadTableLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - LoadTableLambdaVersion5fr0DX1HHGoWLbaJTg0RXRTBadW8LfbMIBmdXQ56k
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Permission - RequestUnicornLambdaPermissionApiGateway
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - RequestUnicornLambdaVersionvLmtICalmdSbSyY1qfPQXgLF1rfMxdYvoT42f0GhXo
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodUnicornGet
CloudFormation - CREATE_IN_PROGRESS - Custom::LoadTable - LoadTable
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - LoadTableLambdaVersion5fr0DX1HHGoWLbaJTg0RXRTBadW8LfbMIBmdXQ56k
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Permission - RequestUnicornLambdaPermissionApiGateway
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodUnicornGet
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - LoadTableLambdaVersion5fr0DX1HHGoWLbaJTg0RXRTBadW8LfbMIBmdXQ56k
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - RequestUnicornLambdaVersionvLmtICalmdSbSyY1qfPQXgLF1rfMxdYvoT42f0GhXo
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Method - ApiGatewayMethodUnicornGet
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - RequestUnicornLambdaVersionvLmtICalmdSbSyY1qfPQXgLF1rfMxdYvoT42f0GhXo
CloudFormation - CREATE_IN_PROGRESS - Custom::LoadTable - LoadTable
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Deployment - ApiGatewayDeployment1536099832325
CloudFormation - CREATE_COMPLETE - Custom::LoadTable - LoadTable
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Deployment - ApiGatewayDeployment1536099832325
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Deployment - ApiGatewayDeployment1536099832325
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Permission - RequestUnicornLambdaPermissionApiGateway
CloudFormation - UPDATE_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - wild-rydes-ride-fleet-dev
CloudFormation - UPDATE_COMPLETE - AWS::CloudFormation::Stack - wild-rydes-ride-fleet-dev
Serverless: Stack update finished...
Service Information
service: wild-rydes-ride-fleet
stage: dev
region: us-east-1
stack: wild-rydes-ride-fleet-dev
api keys:
  None
endpoints:
  GET - https://4xihl63ff9.execute-api.us-east-1.amazonaws.com/dev/unicorn
functions:
  RequestUnicorn: wild-rydes-ride-fleet-dev-RequestUnicorn
  LoadTable: wild-rydes-ride-fleet-dev-LoadTable

Stack Outputs
RequestUnicornLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:144121712529:function:wild-rydes-ride-fleet-dev-RequestUnicorn:6
LoadTableLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:144121712529:function:wild-rydes-ride-fleet-dev-LoadTable:6
RequestUnicornUrl: https://4xihl63ff9.execute-api.us-east-1.amazonaws.com/dev/unicorn
ServiceEndpoint: https://4xihl63ff9.execute-api.us-east-1.amazonaws.com/dev
ServerlessDeploymentBucketName: wild-rydes-ride-fleet-de-serverlessdeploymentbuck-1ndj0rcyltqzc
```
</p>
</details>

### 2. Deploy wild-rydes

Deploy _wild-rydes_. This composed of a RESTful web API that fetches an available ride from the wild-rydes-ride-fleet and the website frontend used by users. The service is composed of API Gateway, an AWS Lambda function, static web content served from an S3 bucket, and a DNS record in Route53.

Clone the GitHub repository, change into the directory, use NodeJS's _npm_ to install Serverless Framework plugins and deploy.

```
$ cd $WORKSHOP
$ git clone https://github.com/ServerlessOpsIO/wild-rydes.git
$ cd wild-rydes
$ npm install
$ sls deploy -v
```
<details>
<summary><strong>Output</strong></summary>
<p>

```
$ cd $WORKSHOP

$ git clone https://github.com/ServerlessOpsIO/wild-rydes.git
Cloning into 'wild-rydes'...
remote: Enumerating objects: 157, done.
remote: Total 157 (delta 0), reused 0 (delta 0), pack-reused 157
Receiving objects: 100% (157/157), 9.46 MiB | 6.68 MiB/s, done.
Resolving deltas: 100% (31/31), done.

$ cd wild-rydes

$ npm install
npm notice created a lockfile as package-lock.json. You should commit this file.
added 77 packages in 6.546s

$ sls deploy -v
Serverless: Installing requirements of requirements.txt in .serverless...
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Injecting required Python packages to package...
Serverless: Creating Stack...
Serverless: Checking Stack create progress...
CloudFormation - CREATE_IN_PROGRESS - AWS::CloudFormation::Stack - wild-rydes-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_COMPLETE - AWS::CloudFormation::Stack - wild-rydes-dev
Serverless: Stack create finished...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service .zip file to S3 (11.45 MB)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - wild-rydes-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - StaticSiteConfig
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - LoadTableLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - RequestRideLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::DynamoDB::Table - UnicornsTable
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - StaticSiteConfig
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - StaticSiteConfigLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - LoadTableLogGroup
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - LoadTableLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::RestApi - ApiGatewayRestApi
CloudFormation - CREATE_IN_PROGRESS - AWS::DynamoDB::Table - UnicornsTable
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - RequestRideLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - StaticSite
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::RestApi - ApiGatewayRestApi
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - RequestRideLogGroup
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::RestApi - ApiGatewayRestApi
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - StaticSiteConfigLogGroup
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - StaticSiteConfigLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - StaticSite
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Resource - ApiGatewayResourceRide
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Resource - ApiGatewayResourceRide
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Resource - ApiGatewayResourceRide
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodRideOptions
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodRideOptions
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Method - ApiGatewayMethodRideOptions
CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - StaticSiteConfig
CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - StaticSite
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - StaticSiteConfigS3BucketPolicy
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - StaticSiteConfigS3BucketPolicy
CloudFormation - CREATE_COMPLETE - AWS::S3::BucketPolicy - StaticSiteConfigS3BucketPolicy
CloudFormation - CREATE_IN_PROGRESS - AWS::Route53::RecordSet - DnsRecord
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - StaticSiteS3BucketPolicy
CloudFormation - CREATE_IN_PROGRESS - AWS::Route53::RecordSet - DnsRecord
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - StaticSiteS3BucketPolicy
CloudFormation - CREATE_COMPLETE - AWS::S3::BucketPolicy - StaticSiteS3BucketPolicy
CloudFormation - CREATE_COMPLETE - AWS::DynamoDB::Table - UnicornsTable
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_COMPLETE - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - LoadTableLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - StaticSiteConfigLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - RequestRideLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - LoadTableLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - LoadTableLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - StaticSiteConfigLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - RequestRideLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - RequestRideLambdaFunction
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - StaticSiteConfigLambdaFunction
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Permission - RequestRideLambdaPermissionApiGateway
CloudFormation - CREATE_IN_PROGRESS - Custom::ConfigFile - StaticSiteConfigUpdate
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - LoadTableLambdaVersiontTVK4z5UeeOMyp9R4QnfvFzUpTOw2oHzzcg268zTw
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Permission - RequestRideLambdaPermissionApiGateway
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodRidePost
CloudFormation - CREATE_IN_PROGRESS - Custom::LoadTable - LoadTable
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - RequestRideLambdaVersionaBUhPmiF7ppczspapO13jnbpEnzfdgEtJdCLcpFrY
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodRidePost
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - StaticSiteConfigLambdaVersionX0Ft6jqlyeWegBmfRrGOqjJIGY5X1xR4LdmE8PSUrQ
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Method - ApiGatewayMethodRidePost
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - LoadTableLambdaVersiontTVK4z5UeeOMyp9R4QnfvFzUpTOw2oHzzcg268zTw
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - LoadTableLambdaVersiontTVK4z5UeeOMyp9R4QnfvFzUpTOw2oHzzcg268zTw
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - RequestRideLambdaVersionaBUhPmiF7ppczspapO13jnbpEnzfdgEtJdCLcpFrY
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - RequestRideLambdaVersionaBUhPmiF7ppczspapO13jnbpEnzfdgEtJdCLcpFrY
CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - StaticSiteConfigLambdaVersionX0Ft6jqlyeWegBmfRrGOqjJIGY5X1xR4LdmE8PSUrQ
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - StaticSiteConfigLambdaVersionX0Ft6jqlyeWegBmfRrGOqjJIGY5X1xR4LdmE8PSUrQ
CloudFormation - CREATE_IN_PROGRESS - Custom::ConfigFile - StaticSiteConfigUpdate
CloudFormation - CREATE_COMPLETE - Custom::ConfigFile - StaticSiteConfigUpdate
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Deployment - ApiGatewayDeployment1537554087578
CloudFormation - CREATE_IN_PROGRESS - Custom::LoadTable - LoadTable
CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Deployment - ApiGatewayDeployment1537554087578
CloudFormation - CREATE_COMPLETE - Custom::LoadTable - LoadTable
CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Deployment - ApiGatewayDeployment1537554087578
CloudFormation - CREATE_COMPLETE - AWS::Lambda::Permission - RequestRideLambdaPermissionApiGateway
CloudFormation - CREATE_COMPLETE - AWS::Route53::RecordSet - DnsRecord
CloudFormation - UPDATE_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - wild-rydes-dev
CloudFormation - UPDATE_COMPLETE - AWS::CloudFormation::Stack - wild-rydes-dev
Serverless: Stack update finished...
Service Information
service: wild-rydes
stage: dev
region: us-east-1
stack: wild-rydes-dev
api keys:
  None
endpoints:
  POST - https://o8gc4w4202.execute-api.us-east-1.amazonaws.com/dev/ride
functions:
  RequestRide: wild-rydes-dev-RequestRide
  LoadTable: wild-rydes-dev-LoadTable
  StaticSiteConfig: wild-rydes-dev-StaticSiteConfig

Stack Outputs
RequestRideLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:144121712529:function:wild-rydes-dev-RequestRide:10
StaticSiteConfigLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:144121712529:function:wild-rydes-dev-StaticSiteConfig:10
LoadTableLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:144121712529:function:wild-rydes-dev-LoadTable:10
StaticSiteS3BucketName: wild-rydes-user0.dev.training.serverlessops.io
StaticSiteS3BucketWebsiteURL: http://wild-rydes-user0.dev.training.serverlessops.io
ServiceEndpoint: https://o8gc4w4202.execute-api.us-east-1.amazonaws.com/dev
ServerlessDeploymentBucketName: wild-rydes-dev-serverlessdeploymentbucket-fq6bas8nsgb0

S3 Sync: Syncing directories and S3 prefixes...
...........
S3 Sync: Synced.
```
</p>
</details>

### 3. Navigate To Application

Navigate to the newly deployed application. In the output of the previous step, look for the _StaticSiteS3BucketWebsiteURL_ in _Stack Outputs_. This is the URL of the newly deployed application.  Navigate to it in a web browser. Request a ride and ensure the process is successful.


![Wild Rydes Web Site](../../images/wild-rydes-site.png)


### 4. Tail application logs

Tail the Lambda function logs from the _wild-rydes_ service. Serverless Framework's `logs` command will poll and dump a Lambda function's logs from CloudWatch to the terminal window.

Start by getting the list of functions in the application stack using Serverless Framework's `info` command.

```
$ cd $WORKSHOP/wild-rydes
$ sls info
```
<details>
<summary><strong>Output</strong></summary>
<p>

```
Service Information
service: wild-rydes
stage: dev
region: us-east-1
stack: wild-rydes-dev
api keys:
  None
endpoints:
  POST - https://a0wh3ig8vh.execute-api.us-east-1.amazonaws.com/dev/ride
functions:
  RequestRide: wild-rydes-dev-RequestRide
  LoadTable: wild-rydes-dev-LoadTable
  StaticSiteConfig: wild-rydes-dev-StaticSiteConfig
```
</p>
</details>

The function's name is under the _functions_ key and called _RequestRide_. We'll ignore _LoadTable_ and _StaticSiteConfig_ for now.

Dump the `RequestRide` logs. This will show the log output from usage of the application in the previous step. After you begin tailing the function's logs request a ride from the website and see the log lines appear in your console.

```
$ sls logs -f RequestRide
```

<details>
<summary><strong>Output</strong></summary>
<p>

```
START RequestId: 77b19fd4-b0a2-11e8-b482-8d4eb39f3e0a Version: $LATEST
2018-09-05 00:27:27.772 (+00:00)        77b19fd4-b0a2-11e8-b482-8d4eb39f3e0a    [INFO]  Starting new HTTPS connection (1): o51ha7h9fa.execute-api.us-east-1.amazonaws.com
END RequestId: 77b19fd4-b0a2-11e8-b482-8d4eb39f3e0a
REPORT RequestId: 77b19fd4-b0a2-11e8-b482-8d4eb39f3e0a  Duration: 857.58 ms     Billed Duration: 900 ms         Memory Size: 128 MB     Max Memory Used: 24 MB

START RequestId: de28da92-b0a2-11e8-8b20-e97d4c435322 Version: $LATEST
2018-09-05 00:30:19.339 (+00:00)        de28da92-b0a2-11e8-8b20-e97d4c435322    [INFO]  Starting new HTTPS connection (1): o51ha7h9fa.execute-api.us-east-1.amazonaws.com
END RequestId: de28da92-b0a2-11e8-8b20-e97d4c435322
REPORT RequestId: de28da92-b0a2-11e8-8b20-e97d4c435322  Duration: 381.62 ms     Billed Duration: 400 ms         Memory Size: 128 MB     Max Memory Used: 24 MB
```
</p>
</details>

If you received the error `No existing streams for the function` then either you did not request a ride in the previous step or logs have been delayed in reaching CloudWatch. Go back to Step 3 and request a ride.

If you'd like to tail logs in realtime then use the `-t` flag to tail the log stream. Run the command below and then request a ride from the site. You will see you ride request show up.

```
$ sls logs -f RequestRide -t
```

### 5. Invoke function

Invoke the _RequestRide_ function without going through the application frontend or API Gateway. The file _tests/events/request-ride-event.json_ is a mock API Gateway event that resembles the data that would be passed by API GAteway to the Lambda function.

```
$ sls invoke -f RequestRide -p tests/events/request-ride-event.json
```

<details>
<summary><strong>Output</strong></summary>
<p>

```json
{
    "statusCode": 201,
    "body": "{\"RideId\": \"30c565ea-a494-11e8-a910-425746ae81de\", \"Unicorn\": {\"Name\": \"Shadowfax\", \"Color\": \"White\", \"DeviceId\": \"21fc3d3a-f26a-11e8-9109-8c859074f8c7\"}, \"RequestTime\": \"2018-08-20 16:15:01.515825\"}",
    "headers": {
        "Access-Control-Allow-Origin": "*"
    }
}
```
</p>
</details>

## Questions

### 1. Serverless Framework

Q. What do each of these subcommands of Serverless framework do?

* deploy
  * How does the `-v` flag effect output?
* info
  * How does the `-v` flag effect output?
* logs
  * How does the `-t` flag effect output?
* invoke
  * How does the `-t` flag effect invocation?

<details>
<summary><strong>Hint</strong></summary>
<p>

* [Serverless Framework CLI Reference](https://serverless.com/framework/docs/providers/aws/)
</p>
</details>
<details>
<summary><strong>Answer</strong></summary>
<p>

* deploy
  * `--verbose` or `-v` shows all stack events during deployment, and display any Stack Output.
* info
  * `--verbose` or `-v` shows displays any Stack Output.
* logs
  * `--tail` or `-t`  will tail the logs and keep listening for new logs in your terminal session.
* logs
  * `--type` or `-t` indicates request type. Can be: RequestResponse, Event or DryRun.
</p>
</details>

### 2. Service Discovery

Q. How does _wild-rydes_ know the _wild-rydes-ride-fleet_ API endpoint?

Where is the HTTP endpoint specified in _wild-rydes_ for the _wild-rydes-ride-fleet_ API endpoint and how does _RequestRide_ know to use it?

<details>
<summary><strong>Hint</strong></summary>
<p>

Serverless Framework has a variety of ways to declare variables.

* [Serverless Framework - Variables](https://serverless.com/framework/docs/providers/aws/guide/variables/)
</p>
</details>

<details>
<summary><strong>Answer</strong></summary>
<p>

In the _serverless.yml_ file for _wild-rydes_ we lookup the RequestUnicornUrl CloudFormation stack output for the _wild-rydes-ride-fleet_ service.

```yaml
custom:
  stage: "${opt:stage, env:SLS_STAGE, 'dev'}"
  log_level: "${env:LOG_LEVEL, 'INFO'}"

  request_unicorn_url: "${cf:wild-rydes-ride-fleet-${self:custom.stage}.RequestUnicornUrl}"
```

Further down in the functions section we set an environmental variable called *REQUEST_UNICORN_URL*.
```yaml
functions:
  RequestRide:
    handler: handlers/request_ride.handler
    description: "Request a ride."
    memorySize: 128
    timeout: 29
    environment:
      REQUEST_UNICORN_URL: "${self:custom.request_unicorn_url}"
    events:
      - http:
          path: /ride
          method: post
          cors: true
```

Finally, *handlers/request_ride.py* reads that environmental variable on startup.

```python
REQUEST_UNICORN_URL = os.environ.get('REQUEST_UNICORN_URL')

def _get_unicorn(url=REQUEST_UNICORN_URL):
    '''Return a unicorn from the fleet'''
    unicorn = requests.get(REQUEST_UNICORN_URL)
    return unicorn.json()
```
</p>
</details>


Q. Name an alternative method of service discovery using only AWS services.
<details>
<summary><strong>Answer</strong></summary>
<p>

The [AWS Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html) service is one way if storing this information. This service let's you store key/value pairs which can be looked up using using [Serverless Framework](https://serverless.com/framework/docs/providers/aws/guide/variables/#reference-variables-using-the-ssm-parameter-store). You can even have a service create a key/value pair using [CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ssm-parameter.html).
</p>
</details>

**Extra Credit:** Implement the solution to the previous question.
<details>
<summary><strong>Answer</strong></summary>
<p>

Option 1: Obtain AWS SSM Param Store value at deploy time. See the _Outputs_ section in _serverless.yml_ to figure out how to get the API endpoint value.

* [AWS::SSM::Parameter](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ssm-parameter.html)
* [Serverless Framework Variables: Reference Variables using the SSM Parameter Store](https://serverless.com/framework/docs/providers/aws/guide/variables/#reference-variables-using-the-ssm-parameter-store)

Option 2: Obtain AWS SSM Param store value at function runtime.

* [ssm-cache-python](https://github.com/alexcasalboni/ssm-cache-python)

</p>
</details>

### 3. Relationship between S3 bucket and Route53 record.

Q. Explain the relationship between the S3 bucket hosting the site and Route53 for DNS resolution. (Hint: Look at the bucket name and compare it with the Route53 DNS record name. use `sls info -v` for that information.)
<details<details>
<summary><strong>Hint</strong></summary>
<p>

* [Setting up a Static Website Using a Custom Domain](https://docs.aws.amazon.com/AmazonS3/latest/dev/website-hosting-custom-domain-walkthrough.html)
</p>
</details>

<details>
<summary><strong>Answer</strong></summary>
<p>

Our website frontend uses S3's static website hosting capabilities. This requires the name of the S3 bucket to be a fully qualified domain name and for is to create a DNS record on a Route53 zone of ours.

The relevant _serverless.yml_ configuration is here:

```yaml
custom:
  hostedZoneName: "${env:SLS_HOSTED_ZONE_NAME, 'dev.training.serverlessops.io'}"
  bucketName: "${self:service}-${self:custom.stage}.${self:custom.hostedZoneName}"
```

```yaml
    StaticSite:
      Type: AWS::S3::Bucket
      Properties:
        AccessControl: PublicRead
        BucketName: ${self:custom.bucketName}
        WebsiteConfiguration:
          IndexDocument: index.html
          ErrorDocument: error.html
```

```yaml
    DnsRecord:
      Type: "AWS::Route53::RecordSet"
      Properties:
        AliasTarget:
          DNSName: s3-website-us-east-1.amazonaws.com
          # Additional region zone IDs and DNS names found here:
          # https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region
          HostedZoneId: Z3AQBSTGFYJSTF    # us-east-1
        HostedZoneName: ${self:custom.hostedZoneName}.
        Name:
          Ref: StaticSite
        Type: 'A'
```
</p>
</details>

### 4. Security

Q. Why doesn't the frontend use HTTPS?
<details>
<summary><strong>Answer</strong></summary>
<p>

The SSL certificate for S3 only supports Amazon S3's own domain names. To use an SSL cert with our own domain name we'd need to use AWS CloudFront as our CDN and have it serve content from our S3 bucket. Deploying CloudFront can be time consuming so it was dropped from this module.
</p>
</details>

Q. What are some security issues with this application deployment.

<details>
<summary><strong>Answer</strong></summary>
<p>
Some of note are:

* There's no account verification or even signup.
* _wild-rydes-ride-requests_ and _wild-rides-ride-fleet_ APIs have no authentication and authorization on them.
* the aforementioned lack of SSL.

</p>
</details>

