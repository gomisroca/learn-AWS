# 🤯 Serverless Mindset

- In a normal setup, as we scale up, we will need to add more and more servers, which will increase the cost, even if the servers are idle. In serverless, we only provision the resources we need, and we pay only for the resources we use.
- In Serverless, we will manage our app and code, as well as the infrastructure, such as health checks, scaling policies, etc. AWS will handle most of the infrastructure management for us.

## 🤔 How Can Serverless Help?

- Normally we can think of HTTP Requests, Business Logic, and Database as the essential components of an application.
- We can think of HTTP Requests as Events, Business Logic as Handlers, and the Database as a Backend.
- In AWS Lambda, we will have Event Sources (Events), Lambda Functions (Handlers), and something like DynamoDB (Backend) or Kinesis Data Streams (Backend).
- To deploy Lambda functions:
  1. Write code.
  2. Compress into a zip file.
  3. Deploy the zip file.
- Serverless means:
  - No server management.
  - Flexible scaling.
  - Automated high availability.
  - No idle costs.

## 🐕‍🦺 Managed Services Connected by Functions

- There are many more managed services that deal with serverless besides Lambda.
- We can use these services as Lambda event sources.
- Each lambda function should be independent and focused on a single task.

## ⏰ From Hours to Minutes with Parallelization

- We can often parallelize our tasks to reduce the time it takes to complete a task.
- Due to the Lambda pricing, this parallelization is possible and cost effective.
