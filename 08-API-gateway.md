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
