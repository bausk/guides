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

### Setting Up a Cloud Provider

We're going to use several Amazon CLI tools for deployments. Use the [Setting Up Providers](../providers.md) guide.

After you're finished setting up Amazon IAM and setting up the project, you're going to have `eb` and `zappa` CLI commands ready to use.

### AWS Elastic Beanstalk

This initializes a new Python 3.6 app in your folder, creates a `development` environment and deploys your app with entrypoint defined in `.ebextensions` of the sample repo, and opens the site:

```
eb init -p python-3.6 APPNAME --region eu-west-1
eb create development
eb open
```


#### Gotchas:

https://docs.aws.amazon.com/en_us/elasticloadbalancing/latest/userguide/elb-api-permissions.html

https://stackoverflow.com/questions/51597410/aws-eks-is-not-authorized-to-perform-iamcreateservicelinkedrole

#### Resources:

[Deploying Dash to AWS EBS](https://www.phillipsj.net/posts/deploying-dash-to-elastic-beanstalk)

[As single container Docker to get Python 3.6](https://docs.aws.amazon.com/en_us/elasticbeanstalk/latest/dg/single-container-docker.html)

### AWS Lambda

Lambdas are supposed to live around 5 minutes so they don't quite fit into a Python Dashboard-style application
where user actions are piped back to backend via websockets. There are solutions to this but the overall process in cumbersome.

#### Gotchas:

- Add prefix to be able to serve static files to the corresponding environments.

- Expose `app.server` as variable and point Zappa to it, otherwise the Dash app won't deploy.


### AWS Orchestration

Using custom domain (Route53) with AWS Lambda is a bit tricky and [requires configuring CloudFront](https://medium.com/99xtechnology/full-stack-serverless-web-apps-with-aws-189d87da024a). Django has a [walkthrough](https://edgarroman.github.io/zappa-django-guide/walk_static/) dedicated to this topic.

# Other

https://github.com/anaibol/awesome-serverless

[Grand scheme app](http://jmdaignan.com/2018/02/26/metricsdash/)

