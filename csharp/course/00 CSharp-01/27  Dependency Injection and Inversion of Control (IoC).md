Dependency Injection (DI) and Inversion of Control (IoC) are fundamental concepts in software development that promote loose coupling, modularity, and testability by decoupling dependencies from the classes that use them. In .NET Core C#, you can implement DI and IoC using the built-in dependency injection container provided by the framework. Here's how you can use DI and IoC in .NET Core C#:

### Dependency Injection (DI)

Dependency Injection is a design pattern where dependencies of a class are provided from the outside rather than created within the class itself.

#### 1. Define Dependencies

```csharp
public interface IEmailService
{
    void SendEmail(string to, string subject, string body);
}

public class EmailService : IEmailService
{
    public void SendEmail(string to, string subject, string body)
    {
        // Send email implementation
    }
}
```

#### 2. Inject Dependencies

```csharp
public class UserService
{
    private readonly IEmailService _emailService;

    public UserService(IEmailService emailService)
    {
        _emailService = emailService;
    }

    public void RegisterUser(string email)
    {
        // Register user logic
        _emailService.SendEmail(email, "Welcome", "Welcome to our platform!");
    }
}
```

#### 3. Configure Dependency Injection Container

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddTransient<IEmailService, EmailService>();
    services.AddTransient<UserService>();
}
```

### Inversion of Control (IoC)

Inversion of Control is a principle where the control of object creation and lifecycle management is inverted from the application to an external framework or container.

#### 1. Configure IoC Container

```csharp
var serviceProvider = new ServiceCollection()
    .AddTransient<IEmailService, EmailService>()
    .AddTransient<UserService>()
    .BuildServiceProvider();
```

#### 2. Resolve Dependencies

```csharp
var userService = serviceProvider.GetService<UserService>();
```

### Benefits of DI and IoC

- **Decoupling**: Classes are decoupled from their dependencies, making them easier to maintain and test.
- **Modularity**: Dependencies can be easily swapped or replaced, promoting modularity and flexibility.
- **Testability**: Classes can be easily tested in isolation by providing mock or fake dependencies.

### Using Built-in DI Container in ASP.NET Core

ASP.NET Core provides a built-in DI container that automatically resolves dependencies for controllers, services, and other components registered in the container. You can use constructor injection in controllers and services to inject dependencies.

```csharp
public class MyController : Controller
{
    private readonly IUserService _userService;

    public MyController(IUserService userService)
    {
        _userService = userService;
    }
}
```

### Summary

Dependency Injection and Inversion of Control are powerful concepts that promote loose coupling, modularity, and testability in .NET Core C# applications. By using DI and IoC, you can write more maintainable, flexible, and scalable code. Let me know if you need further clarification or more examples!