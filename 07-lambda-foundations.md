# AWS Lambda Foundations

## Intro to Serverless

- With serverless, AWS handles everything required to run and scale the app.
- Lambda is a compute service that runs your code in response to events.
- Benefits of Lambda:
  - No need for provisioning or managing servers.
  - Initiates execution of code in response to events.
  - Scales automatically.
  - Built-in monitoring and logging.
  - Integration with other AWS services.
  - Flexible permissions model.
  - Pay only for the resources you use.
  - Availability and fault tolerance built-in.
- Event-driven architecture uses observable events to initiate actions and communication between different services.
- The architecture consists of Event Producers (app, website, etc.), Event Routers (ingests events and directs it to the appropriate consumers), and Event Consumers (database, financial system, customer service, etc.).

## How AWS Lambda Works

- Event sources can invoke Lambda functions in three general patterns:
  - Synchronous invocation: Lambda runs the fn and waits for a response. An immediate response is expected. Errors: no retries.
  - Asynchronous invocation: Events are queued and a response is not waited on. Errors: retries twice.
  - Polling invocation: Designed to integrate with other AWS services. AWS will manage the polling and perform synchronous invocations. Errors: depends on source.
- Lambda functions are invoked in an isolated and secure execution environment. This environment manages resources and provides support for the fn's runtime.
- It is best practice to minimize cold starts. That is, requiring a new environment to run the fn. This adds latency. We should use warm starts, where the environment is retained between invocations. There's also Provisioned Concurrency, a Lambda feature that prepares environments before a function is invoked.
- To take advantage of warm starts:
  1. Sore and reference dependencies locally.
  2. Limit reinit of vars.
  3. Add checks for existing connections.
  4. Use tmp space as transient cache.
  5. Check that background processes have completed.

## AWS Lambda Function Permissions

- Need two types of permissions: permission to invoke the fn, and permission for the Lambda fn itself to act upon other AWS services.
- Invoke permissions are controlled using IAM resource policies.
  - Tells Lambda which principals (user, role, service) can invoke the fn.
  - Can be seen and modified from the Lambda console.
  - It has a principal size limits.
- Function permissions are controlled using IAM execution roles.
  - Role is provided when creating the function.
  - The policy attached to the role determines what the function can do.
  - It must include a trust police that allows Lambda to "AssumeRole".
  - Can be written or use provided roles.
  - Can edit permissions at any time.
- Should follow the principle of least privilege.
- If the Lambda fn needs access to a resource within a VPC, it needs VPC-specific information, such as VPC subnet IDs and security group IDs. The execution role will be "AWSLambdaVPCAccessExecutionRole".

## Authoring AWS Lambda Functions

- Can be written in almost any language.
- The handler fn is the entry point for the fn. When the fn is invoked, the handler fn is called.
- The handlers takes an event object and a context object as parameters.
  - The event obj is required.
  - The event obj includes all the data to make the fn work.
  - The context obj is optional.
  - The context obj allows the fn to interact with the execution environment.
- It is best practice to separate business logic from the handler method.
- Serverless applications should treat each function as stateless. No information should be stored in the function.

## Configuring AWS Lambda Functions

- Three primary config settings:
  - Memory: Up to 10GB. More memory size = more CPU.
  - Timeout: Max 900s. Billed on 1ms increments.
  - Concurrency: If the fn is invoked while another request is in progress, another instance will be allocated. Limit concurrency to regulate costs, reserve concurrency to ensure the fn can handle peak load.
- To test:
  - Run performance tests to simulate peak load.
  - Test if the existing backend is able to handle the load.
  - Test the error handling.
