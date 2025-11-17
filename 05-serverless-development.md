# 💻 Introduction to Serverless Development

- Serverless architecture helps with managing costs, reduces the engineering effort necessary, and enables rapid development.
- AWS Lambda is a serverless compute service that runs code in response to events.

## 🐑 Writing Lambda Functions

- Every lambda function has a handler method. It is the entry point for the lambda function.
- Just like with regular code, we should split the code into smaller functions.
- Typically, we put the Lambda specific code in the handler method, and any business logic into a controller class responsible for handling the event.
- Service classes can be used to abstract any external dependencies.

## 🤹 Managing Serverless Applications

- During serverless development, we need to manage multiple lambda functions and resources.
- Can use frameworks like AWS SAM to simplify the building, packaging, configuring, and deploying of serverless applications.
- SAM and similar frameworks provides CLI tools to automate packaging and deployment.
- Instead of organizing repos by function, we can organize them by service. A service can have multiple Lambda functions.
- Should provide AWS sandbox environments to test code, either per-developer or shared.
- Keep production and non-production environments in separate accounts.
