# Python Deployment to Serverless Providers

I wanted to try a serverless, modern Python deployment pipeline. As a reference, an example Dash by Plotly project was used.
This is what I've discovered so far.

### Setting Up the Project

Install pipenv. To make it maximally robust, do it in [the following fashion](https://github.com/Miserlou/Zappa/issues/1443) to keep the virtual environment recognizable by tools like `zappa`:
```
export PIPENV_VENV_IN_PROJECT=true
pip install pipenv
pipenv install
export VIRTUAL_ENV=.venv/
```

Now you can install development dependencies, like CLI tools for Amazon Web Services, `eb` and `aws`.

`aws elasticbeanstalk list-available-solution-stacks`

### Source Application

[Simple callback, working on Lambda:](https://dash.plot.ly/sharing-data-between-callbacks)

[Grand scheme app](http://jmdaignan.com/2018/02/26/metricsdash/)

### AWS Lambda is not a Good Choice For Websocket-Based Stuff

Lambdas are supposed to live around 5 minutes so they don't quite fit into a Python Dashboard-style application
where user actions are piped back to backend via websockets. There are solutions to this but the overall process in cumbersome.

#### Reference links of interest:

- TBD

#### Gotchas:

- Add prefix to be able to serve static files to the corresponding environments.

- Expose `app.server` as variable and point Zappa to it, otherwise the Dash app won't deploy.

### AWS Elastic Beanstalk

Resources:

[Deploying Dash to AWS EBS](https://www.phillipsj.net/posts/deploying-dash-to-elastic-beanstalk)

[As single container Docker to get Python 3.6](https://docs.aws.amazon.com/en_us/elasticbeanstalk/latest/dg/single-container-docker.html)

#### Gotchas:

https://docs.aws.amazon.com/en_us/elasticloadbalancing/latest/userguide/elb-api-permissions.html

https://stackoverflow.com/questions/51597410/aws-eks-is-not-authorized-to-perform-iamcreateservicelinkedrole

### AWS Orchestration

Using custom domain (Route53) with AWS Lambda is a bit tricky and [requires configuring CloudFront](https://medium.com/99xtechnology/full-stack-serverless-web-apps-with-aws-189d87da024a). Django has a [walkthrough](https://edgarroman.github.io/zappa-django-guide/walk_static/) dedicated to this topic.

# Other

https://github.com/anaibol/awesome-serverless
