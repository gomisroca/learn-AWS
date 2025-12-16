# Amazon API Gateway for Serverless Applications

## Intro to API Gateway

- API Gateway facilitates the creation and management of APIs at any scale.
- It handles requests, traffic, CORS, authorization, access control, and more.
- Developer features:
  - Run multiple versions of an API simultaneously.
  - Quick SDK generation.
  - Transform/validate request-response data.
- Features for managing API access:
  - Reduce latency and throttle traffic.
  - Built-in authorization options.
  - API keys for third-party devs.

## Designing WebSocket APIs

- In a WebSocket API, the client and server can communicate in real-time.
- In API Gateway, we can create a WebSocket API as a stateful frontend for an AWS service.
- API Gateway will manage the persistence and state needed to connect the client and server.
- We only pay when the API is used.
- We need at least one route, integration and stage before deploying the API.
- Three predefined routes: $connect, $disconnect, and $default. Can add custom routes.
- The route must be integrated with an endpoint, which can be something like a Lambda function or a service action.
- To set up an integration request:
  - Choose a route.
  - Choose the endpoint.
  - Configure how to transform the request data if necessary.

## Designing REST APIs

- A REST API in API Gateway is a collection of resources and methods integrated with backend endpoints, Lambda functions, or other AWS services.
- We need to decide the type of endpoint:
  - Regional: reduced latency within a region.
  - Edge-optimized: reduced client latency.
  - Private: only exposes API inside VPC.
- We can cache the endpoint responses.

## Building and Deploying APIs with API Gateway

- When we deploy an API to a stage, a base URL is generated. That's the invoke URL.
- Can add a custom domain as the host to make the URL more user-friendly.
- Steps to build an API with API Gateway:
  - Choose API type.
  - Create API.
  - Add resources.
  - Configure resource as proxy.
  - Create method.
  - Edit method details.
  - Test your API methods.
- A stage is a snapshot of the API.
- Best practices:
  - Use stages with Lambda aliases.
  - Use Canary deployments.
  - Use AWS SAM to simplify deployment.

## Managing API Access

- API Gateway provides options for authorizing access to APIs, providing granular control, and controlling the amount of access through throttling.
- Three ways to authorize access:
  - IAM and Sig v4.
    - Good for internal services or restricted number of users.
  - Lambda Authorizers.
    - Supports bearer token strategies such as OAuth.
    - Can use API Gateway Lambda Authorizer blueprint for a quick start.
    - Simply a Lambda fn that performs any custom authorization we write.
  - Amazon Cognito with Cognito User Pools
- IAM policies: `execute-api` to decide who can invoke the API. `apigateway` to decide who can manage the API.

## Monitoring and Troubleshooting

- Can use CloudWatch metrics to monitor API Gateway. It has 7 metrics by default:
  - Count
  - Latency
  - IntegrationLatency
  - 4xxError
  - 5xxError
  - CacheHitCount
  - CacheMissCount
- Latency and IntegrationLatency are particularly useful to calculate API Gateway overhead of deployed APIs.
- Two types of CloudWatch logs:
  - Execution logs: logs what's happening on the roundtrip of a request.
  - Access logs: logs who's invoking the API.
- Can use X-Ray and CloudTrail to analyze use and performance.
