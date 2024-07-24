Setting up structured logging and monitoring in your .NET Core applications is essential for troubleshooting, performance optimization, and gaining insights into application behavior. Let's see how to set up structured logging with Serilog and monitoring with Application Insights in a .NET Core application.

### Example: Setting up Structured Logging with Serilog and Monitoring with Application Insights

1. Install the necessary NuGet packages:

```bash
dotnet add package Serilog.AspNetCore
dotnet add package Serilog.Settings.Configuration
dotnet add package Serilog.Sinks.Console
dotnet add package Microsoft.ApplicationInsights.AspNetCore
```

2. Configure Serilog and Application Insights in `Program.cs`:

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;
using Serilog;

namespace YourNamespace
{
    public class Program
    {
        public static void Main(string[] args)
        {
            Log.Logger = new LoggerConfiguration()
                .WriteTo.Console()
                .WriteTo.ApplicationInsights("<YOUR_APP_INSIGHTS_INSTRUMENTATION_KEY>")
                .CreateLogger();

            CreateHostBuilder(args).Build().Run();
        }

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseStartup<Startup>();
                })
                .UseSerilog(); // Use Serilog for logging
    }
}
```

3. Configure logging in `appsettings.json`:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information"
    }
  },
  "Serilog": {
    "Using": [ "Serilog.Sinks.Console", "Serilog.Sinks.ApplicationInsights" ],
    "MinimumLevel": "Information",
    "WriteTo": [
      { "Name": "Console" },
      {
        "Name": "ApplicationInsights",
        "Args": {
          "instrumentationKey": "<YOUR_APP_INSIGHTS_INSTRUMENTATION_KEY>"
        }
      }
    ]
  }
}
```

4. Use logging in your application:

```csharp
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Logging;

namespace YourNamespace.Controllers
{
    [ApiController]
    [Route("api/[controller]")]
    public class ExampleController : ControllerBase
    {
        private readonly ILogger<ExampleController> _logger;

        public ExampleController(ILogger<ExampleController> logger)
        {
            _logger = logger;
        }

        [HttpGet]
        public IActionResult Get()
        {
            _logger.LogInformation("This is a log message.");
            // Your action logic
            return Ok();
        }
    }
}
```

5. Deploy your application and navigate to the Azure portal to view monitoring data in Application Insights.

Now, your .NET Core application is set up with structured logging using Serilog, and monitoring data is collected and displayed in Application Insights. You can view logs, track performance metrics, and monitor the health of your application in real-time.