In ASP.NET Core, you can create background tasks and workers using the Hosted Service approach, which allows you to run tasks asynchronously within your application, often in the background. Hosted Services are ideal for tasks like scheduled jobs, background processing, and other long-running operations. Here's how to create background tasks and workers using the Hosted Service approach:

### 1. Create a Hosted Service:

To create a Hosted Service, you need to implement the `IHostedService` interface and override its `StartAsync` and `StopAsync` methods.

```csharp
using System;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

public class MyBackgroundService : IHostedService, IDisposable
{
    private readonly ILogger<MyBackgroundService> _logger;
    private Timer _timer;

    public MyBackgroundService(ILogger<MyBackgroundService> logger)
    {
        _logger = logger;
    }

    public Task StartAsync(CancellationToken cancellationToken)
    {
        _logger.LogInformation("MyBackgroundService is starting.");

        // Set up a timer to execute a method periodically
        _timer = new Timer(DoWork, null, TimeSpan.Zero, TimeSpan.FromSeconds(30));

        return Task.CompletedTask;
    }

    public Task StopAsync(CancellationToken cancellationToken)
    {
        _logger.LogInformation("MyBackgroundService is stopping.");

        // Stop the timer
        _timer?.Change(Timeout.Infinite, 0);

        return Task.CompletedTask;
    }

    private void DoWork(object state)
    {
        _logger.LogInformation("MyBackgroundService is doing some work at " + DateTime.Now);
    }

    public void Dispose()
    {
        _timer?.Dispose();
    }
}
```

### 2. Register the Hosted Service:

In the `Startup.cs` file, register your Hosted Service in the `ConfigureServices` method:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddHostedService<MyBackgroundService>();

    // Other service registrations...
}
```

### 3. Run the Hosted Service:

Your Hosted Service will automatically start and run when your ASP.NET Core application starts. It will execute the `DoWork` method periodically as defined in the timer. You can adjust the timer interval to control how often the background task runs.

This is a simple example, but you can use Hosted Services for more complex background tasks, such as processing queues, sending emails, or performing any long-running operations that should run independently of your web application.

Hosted Services are an excellent way to manage background tasks in an ASP.NET Core application and ensure they run reliably, even if your web application restarts or faces other interruptions.