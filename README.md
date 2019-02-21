# Modern Development for the Web: Guides

Knowledge base on various gotchas and processes in different technology stacks.

YMMV: This repo is not production quality. It's basically a brain dump to pick out information for future talks, seminars, etc. Use at own discretion.

## Pre-Requisites

The list of stuff you need to install before going through with the guides has two parts: mandatory and opinionated. I try to maintain a uniform stack of tools on all projects and use Windows 10.

## Contents

### Prerequisites

- [Setting up Cloud Providers for Local Development](providers.md)

### Python

All Python tutorials have the [onilapp example application](https://github.com/bausk/onilapp) as a source example. You can just start with the first onw.

- [Starting and Deploying a Python Project](python/01_start_and_deployment.md)

- [Consuming Data for Production in Python Apps](python/02_consuming_data.md)

- [Deploying to AWS Lambda with Zappa](python/03_awslambda.md) (deprecated, use `sls` below)

- [Deploying to AWS Lambda with Serverless Framework](python/04_serverless.md)

- [Static Deploys](python/05_staticdeploys.md)

### JAMStack

After I was done with building an MVP with Dash in Python, I tried to split up the app components into a JAMStack architecture. The notes documenting this start here.

- [JAMStack Intro](jamstack/01_intro.md)

### Containerization

- [How Do I... in Docker](containers/docker.md)

- [Using Kubernetes for Web Development](containers/k8s.md)
