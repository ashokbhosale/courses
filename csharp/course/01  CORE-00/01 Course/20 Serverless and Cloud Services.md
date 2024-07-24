Serverless computing allows you to build and run applications and services without having to manage infrastructure. Azure Functions and AWS Lambda are popular serverless computing platforms that enable you to execute code in response to events without worrying about server management. Let's explore serverless computing using Azure Functions and deployment/scaling with cloud services.

### Example: Serverless Computing with Azure Functions using .NET Core C#

1. Create an Azure Functions project:

```bash
dotnet new func --name MyFunctionApp --language "C#"
cd MyFunctionApp
```

2. Implement a simple HTTP-triggered function:

```csharp
using Microsoft.AspNetCore.Mvc;
using Microsoft.Azure.WebJobs;
using Microsoft.Azure.WebJobs.Extensions.Http;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.Logging;
using System.Threading.Tasks;

namespace MyFunctionApp
{
    public static class MyFunction
    {
        [FunctionName("MyFunction")]
        public static async Task<IActionResult> Run(
            [HttpTrigger(AuthorizationLevel.Function, "get", "post", Route = null)] HttpRequest req,
            ILogger log)
        {
            log.LogInformation("C# HTTP trigger function processed a request.");

            string name = req.Query["name"];

            return new OkObjectResult($"Hello, {name}");
        }
    }
}
```

3. Deploy the Azure Function to Azure:

```bash
func azure functionapp publish <FunctionAppName>
```

### Deployment and Scaling with Azure:

1. Deploy your .NET Core application to Azure App Service:

```bash
az webapp up --sku F1 --name <AppServiceName> --resource-group <ResourceGroupName>
```

2. Scale your application manually or automatically based on demand:

```bash
az appservice plan update --name <AppServicePlanName> --resource-group <ResourceGroupName> --sku S1 --number-of-workers 2
```

### Example: Serverless Computing with AWS Lambda using .NET Core C#

1. Install the AWS Toolkit for Visual Studio.

2. Create a new AWS Lambda project using the AWS Lambda Project template.

3. Implement a simple Lambda function:

```csharp
using Amazon.Lambda.Core;

[assembly: LambdaSerializer(typeof(Amazon.Lambda.Serialization.SystemTextJson.DefaultLambdaJsonSerializer))]

namespace MyLambdaFunction
{
    public class Function
    {
        public string FunctionHandler(string input, ILambdaContext context)
        {
            context.Logger.LogLine($"Input: {input}");
            return $"Hello, {input}";
        }
    }
}
```

4. Deploy the Lambda function using the AWS Toolkit for Visual Studio.

### Deployment and Scaling with AWS:

1. Deploy your .NET Core application to AWS Lambda using the AWS Toolkit for Visual Studio.

2. Configure auto-scaling policies for your Lambda function based on the number of concurrent executions.

Both Azure Functions and AWS Lambda offer a highly scalable and cost-effective way to run code in response to events without managing servers. Depending on your cloud provider preference and requirements, you can choose either Azure Functions or AWS Lambda for your serverless computing needs.