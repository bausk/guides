# Python Deployment

I wanted to try a serverless, modern Python deployment pipeline. As a reference, an example Dash by Plotly project was used.
This is what I've discovered so far.

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

[As single container Docker to get Python 3.6](https://docs.aws.amazon.com/en_us/elasticbeanstalk/latest/dg/single-container-docker.html)

