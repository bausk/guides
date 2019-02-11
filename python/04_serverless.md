# Deploying to AWS via Serverless

### Prerequisites

You should have the setup from [Python Tutorial](01_start_and_deployment.md).

Install Serverless and dependencies:

```
npm install -g serverless
npm init -f
npm install --save-dev serverless-wsgi serverless-python-requirements
```

### Basic Install

Follow [this tutorial](https://serverless.com/blog/flask-python-rest-api-serverless-lambda-dynamodb/).

Main problem is going to be reducing the size of the deliverable. Example serverless.yaml to do that is like this in my case:

```
# serverless.yml

service: onillambda

plugins:
  - serverless-python-requirements
  - serverless-wsgi

custom:
  wsgi:
    app: app.app
    packRequirements: false
  pythonRequirements:
    slim: true
    dockerizePip: non-linux
    pythonBin: python

package:
  exclude:
  - .venv/**
  - .idea/**
  - .git/**
  - .ebextensions/**
  - .elasticbeanstalk/**
  - .vscode/**
  - scripts/**  

provider:
  name: aws
  runtime: python3.6
  stage: dev
  region: us-east-1

functions:
  app:
    handler: wsgi_handler.handler
    events:
      - http: ANY /
      - http: 'ANY {proxy+}'
```

This example config is mostly derived from the tutorial above and [another example for Plotly](https://github.com/nafeger/serverless-plotly-example/blob/master/serverless.yml).

If you're getting bucket/role problems, manually delete the stack in [CloudWatch](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks?filter=active), rename the service, and redeploy.

### Adding a Domain Name


### Deploying Plotly Dash

### Adding Database and Authentication

### Adding Secrets
