# 💻 Introduction to Serverless Development

- Serverless architecture helps with managing costs, reduces the engineering effort necessary, and enables rapid development.
- AWS Lambda is a serverless compute service that runs code in response to events.

## 🐑 Writing Lambda Functions

- Every lambda function has a handler method. It is the entry point for the lambda function.
- Just like with regular code, we should split the code into smaller functions.
- Typically, we put the Lambda specific code in the handler method, and any business logic into a controller class responsible for handling the event.
- Service classes can be used to abstract any external dependencies.

## 🤹 Managing Serverless Applications

- Serverless development uses the same coding practices and tooling as traditional development, but adds the need for packaging and deploying multiple Lambda functions and resources.
- Application frameworks like AWS SAM simplify the otherwise complex process of building, packaging, configuring, and deploying serverless applications, reducing large CloudFormation templates to a few lines.
- SAM (and similar frameworks) provides CLI tools to automate packaging and deployment, making it easier to manage applications across environments.
