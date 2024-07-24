**Serverless Computing:**

Serverless computing is a cloud computing model where cloud providers dynamically manage the allocation of machine resources. Developers focus on writing code in the form of functions or microservices, and the cloud provider takes care of infrastructure provisioning, scaling, and maintenance. This allows developers to focus on writing code without worrying about managing servers.

**Developing Serverless Applications using Azure Functions or AWS Lambda with .NET Core:**

Azure Functions and AWS Lambda are serverless compute services provided by Microsoft Azure and Amazon Web Services (AWS) respectively. These services allow you to run code in response to events without provisioning or managing servers.

```csharp
// Example of an Azure Function using .NET Core
public static class HelloWorldFunction
{
    [FunctionName("HelloWorld")]
    public static async Task<IActionResult> Run(
        [HttpTrigger(AuthorizationLevel.Function, "get", "post", Route = null)] HttpRequest req,
        ILogger log)
    {
        log.LogInformation("C# HTTP trigger function processed a request.");

        return new OkObjectResult("Hello, World!");
    }
}
```

This Azure Function responds to HTTP requests by returning a "Hello, World!" message.

```csharp
// Example of an AWS Lambda function using .NET Core
public class HelloWorldFunction
{
    public string FunctionHandler(string input, ILambdaContext context)
    {
        return "Hello, World!";
    }
}
```

This AWS Lambda function returns a "Hello, World!" message.

**Event-driven Architectures and Serverless Patterns:**

Event-driven architectures are common in serverless computing, where functions are triggered by events such as HTTP requests, database changes, or message queue messages. Serverless patterns like event sourcing, command-query responsibility segregation (CQRS), and fan-out/fan-in are often used in conjunction with event-driven architectures.

```csharp
// Example of event-driven Azure Function using Azure Event Grid
public static class ProcessOrderFunction
{
    [FunctionName("ProcessOrder")]
    public static async Task Run(
        [EventGridTrigger] EventGridEvent eventGridEvent,
        ILogger log)
    {
        var eventData = eventGridEvent.Data as JObject;
        var orderId = eventData.GetValue("orderId");

        // Process the order
        log.LogInformation($"Order {orderId} processed successfully.");
    }
}
```

This Azure Function is triggered by events published to Azure Event Grid, allowing for event-driven processing of orders.

Serverless computing enables developers to build scalable and cost-effective applications by leveraging the managed infrastructure provided by cloud providers, such as Azure Functions or AWS Lambda.