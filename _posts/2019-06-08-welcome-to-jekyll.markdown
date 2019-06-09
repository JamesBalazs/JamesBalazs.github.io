---
layout: post
title:  "Dockerize everything"
date:   2019-06-08 16:03:49 +0100
categories: dev
---
Anyone that has had to develop and deploy an application probably knows that it's more trouble than it's worth dealing with dependencies.

You onboard a new team member who needs a dev environment - a whole day is spent trying to install everything they need to get started, and troubleshooting issues runnind dev tools.

Want to run your servers on a different platform, with a different OS? Good luck.

But what if you didn't have to deal with all of these issues? If you Dockerize your app, deploy scripts, and build tools, you don't have to. Preferably, this would be done from the start of a project, but it can be done at any point, as I proved by gradually moving Receptive, Pendo's feedback product, into Docker and Kubernetes.

The idea is that you can install Docker and an IDE on your dev machine, run a single command, and have a fully working dev environment. The same Docker images are deployed in production so that your development environment is as close to production as possible - any incompatible dependencies will be apparent on your local machine before you roll out. Host directories are mounted to allow for live code reloading during development, and code is baked in to images for production, or pulled from Git on rollout. What was once a day of troubleshooting when you hire a Junior Dev is now a simple `git clone` and `docker-compose up`. No more ties to a single infrastructure provider - you could move your app from AWS to GCP, from Heroku to DigitalOcean, without changing any config.
