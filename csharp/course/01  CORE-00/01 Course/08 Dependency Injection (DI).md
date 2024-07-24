**Dependency Injection (DI) in .NET Core:**

Dependency Injection (DI) is a design pattern used to manage dependencies between objects in an application. In .NET Core, the built-in DI container simplifies the implementation of DI by automatically resolving and injecting dependencies into the classes that need them. Let's explore how to use the DI container in .NET Core with an example.

**1. Registering Services:**

The first step in using DI in .NET Core is to register the services (dependencies) with the DI container. This is typically done in the `Startup` class.

```csharp
// Startup.cs
using Microsoft.Extensions.DependencyInjection;

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register services with the DI container
        services.AddTransient<IMessageService, EmailService>();
        services.AddSingleton<ILogger, ConsoleLogger>();
    }
}
```

**2. Injecting Dependencies:**

Once the services are registered, you can inject them into classes that depend on them using constructor injection.

```csharp
// MyClass.cs
public class MyClass
{
    private readonly IMessageService _messageService;
    private readonly ILogger _logger;

    public MyClass(IMessageService messageService, ILogger logger)
    {
        _messageService = messageService;
        _logger = logger;
    }

    public void DoSomething()
    {
        // Use the injected services
        _logger.Log("Doing something...");
        _messageService.SendMessage("Hello, World!");
    }
}
```

**3. Using the DI Container:**

Finally, you can use the DI container to resolve the dependencies and create instances of the classes.

```csharp
// Program.cs
using Microsoft.Extensions.DependencyInjection;

class Program
{
    static void Main(string[] args)
    {
        // Create a service collection
        var services = new ServiceCollection();

        // Configure services
        ConfigureServices(services);

        // Build the service provider
        var serviceProvider = services.BuildServiceProvider();

        // Resolve the class with dependencies
        var myClass = serviceProvider.GetRequiredService<MyClass>();

        // Use the class
        myClass.DoSomething();
    }

    static void ConfigureServices(IServiceCollection services)
    {
        // Register services with the DI container
        services.AddTransient<IMessageService, EmailService>();
        services.AddSingleton<ILogger, ConsoleLogger>();

        // Register the class with dependencies
        services.AddTransient<MyClass>();
    }
}
```

In this example:
- We register `IMessageService` and `ILogger` with the DI container as transient and singleton services, respectively.
- We define a class `MyClass` that depends on `IMessageService` and `ILogger`.
- We configure the DI container in the `ConfigureServices` method of the `Startup` class.
- We use the DI container to resolve `MyClass` and its dependencies in the `Main` method of the `Program` class.

By using DI in .NET Core, you can achieve loose coupling between components, improve testability, and make your codebase more maintainable and scalable.