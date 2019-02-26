# Setting Up

I'll start where we left off with the Serverless Framework. The goal of this guide is to explore how to build a data-driven web application and address common business concerns like authentication, analysis tools usage, and sleek, usable frontend. I'm also trying to demonstrate usage of various modern web technologies while spending as little effort as possible :)

### Setting Goalposts

#### Existing Conditions

We have a small app written in Dash Components (Python wrappers that allow wiring up frontend pages and widgets to a Flask server without actually writing frontend code) that accesses a Google Sheets document, ingests a dataset of sensors from there, and outputs it as a surface on a Dash plot. It's using Flask backend wrapped around Dash and is deployed on AWS Lambda as a monolithic app since that's what Dash does. It looks like this:

![Old app](img/Screenshot_8.png)

If you're not interested in which code in the old app survives the migration to the new stack and which doesn't, you don't need to have the old app repo, I'm starting with a new repo. Otherwise, you may want to [clone the old repo](https://github.com/bausk/onilapp).

#### Desired Outcome

- Static or zero-config-to-serve frontend written in an established React-based framework that requires minimum effort to set up.
- Authentication and authorization. We only want whitelisted users to access the content, and we want to explore solutions

### Things to Consider

We start with an existing app deployed on either AWS Lambda or EBS. These are some issues I considered. I'll spare the details so here's a digest of choices I would consider optimal for a small-to-medium project.

- Q: If I'm going to break up my project into a separate frontend and backend, how should I structure my files?

- A: 
- Should I continue developing by editing the current monolithic repository or start from scratch and move code from the old repo as I go along?

Since I got some errors with Next.js, I provisioned a new certificate for another subdomain and removed the 'create Route53 record' option for `sls`, and it worked like a charm.

Checkout the `v1.4-frontend` tag from our repo.

The reference document for now is [Crash Course on SSR with Next.js and AWS Lambda](https://dev.to/adnanrahic/a-crash-course-on-serverless-side-rendering-with-reactjs-nextjs-and-aws-lambda-13ed).

https://auth0.com/docs/flows/concepts/single-page-login-flow
