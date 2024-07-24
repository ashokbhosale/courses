Dependency injection (DI) is a fundamental concept in ASP.NET Core that helps manage the dependencies of components within your application. Here's how you can use dependency injection in ASP.NET Core with .NET Core:

### 1. Register Services

In ASP.NET Core, you register services with the built-in dependency injection container during application startup. This can be done in the `ConfigureServices` method of the `Startup` class.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Register services
    services.AddSingleton<IMyService, MyService>();
    services.AddScoped<IOtherService, OtherService>();
    services.AddTransient<IRepository, Repository>();
}
```

### 2. Resolve Dependencies

Once services are registered, you can inject them into your controllers, services, or other components using constructor injection.

```csharp
public class MyController : Controller
{
    private readonly IMyService _myService;
    private readonly IOtherService _otherService;

    public MyController(IMyService myService, IOtherService otherService)
    {
        _myService = myService;
        _otherService = otherService;
    }

    // Controller actions
}
```

### 3. Use Dependency Injection in Middleware

You can also inject services into middleware components.

```csharp
public class MyMiddleware
{
    private readonly RequestDelegate _next;
    private readonly IMyService _myService;

    public MyMiddleware(RequestDelegate next, IMyService myService)
    {
        _next = next;
        _myService = myService;
    }

    public async Task Invoke(HttpContext context)
    {
        // Use _myService
        await _next(context);
    }
}
```

### 4. Built-in Container or Custom Containers

ASP.NET Core comes with a built-in dependency injection container (`IServiceCollection`). However, you can also use third-party containers like Autofac or StructureMap if you prefer.

### 5. Lifetime Options

ASP.NET Core supports different service lifetimes:

- **Singleton**: A single instance is created and shared throughout the application's lifetime.
- **Scoped**: A new instance is created for each request within the scope of the request.
- **Transient**: A new instance is created every time the service is requested.

### 6. Additional Features

ASP.NET Core's DI container also supports features like named dependencies, validation, and configuration-based registration.

### Summary

Dependency injection is a powerful feature of ASP.NET Core that promotes loose coupling, testability, and maintainability of your applications. By following these steps, you can effectively use dependency injection in your ASP.NET Core applications with .NET Core. Let me know if you need further assistance or more examples!