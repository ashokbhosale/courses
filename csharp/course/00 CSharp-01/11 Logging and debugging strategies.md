Logging and debugging are essential aspects of software development in .NET Core (and C# in general). Here's an overview of logging and debugging strategies you can use in .NET Core C#:

### Logging

#### 1. Microsoft.Extensions.Logging
.NET Core provides a built-in logging framework through the `Microsoft.Extensions.Logging` namespace. You can configure logging providers like Console, Debug, EventLog, etc., and log messages with different log levels (Information, Warning, Error, etc.).

Example:

```csharp
using Microsoft.Extensions.Logging;

class MyClass
{
    private readonly ILogger _logger;

    public MyClass(ILogger<MyClass> logger)
    {
        _logger = logger;
    }

    public void DoSomething()
    {
        _logger.LogInformation("Doing something...");
    }
}
```

#### 2. Serilog
Serilog is a popular third-party logging library that provides a more flexible and powerful logging experience compared to the built-in logging framework.

Example:

```csharp
using Serilog;

class Program
{
    static void Main(string[] args)
    {
        Log.Logger = new LoggerConfiguration()
            .WriteTo.Console()
            .CreateLogger();

        Log.Information("Hello, Serilog!");

        Log.CloseAndFlush();
    }
}
```

### Debugging

#### 1. Visual Studio Debugger
Visual Studio provides a rich debugging experience with features like breakpoints, watch windows, call stack, and various debugging tools.

#### 2. Console.WriteLine / Debug.WriteLine
For quick and simple debugging, you can use `Console.WriteLine` or `Debug.WriteLine` to output messages to the console or debug output.

Example:

```csharp
Debug.WriteLine("Debug message: " + someVariable);
```

#### 3. DebuggerStepThroughAttribute
You can use the `DebuggerStepThrough` attribute to mark methods or properties that you don't want the debugger to step into during debugging.

Example:

```csharp
[DebuggerStepThrough]
public void SomeMethod()
{
    // Debugging won't step into this method
}
```

#### 4. Logging Frameworks
Logging frameworks like Serilog or Microsoft.Extensions.Logging can also be useful for debugging by logging relevant information during development and troubleshooting.

### Tips

- Use structured logging to include additional context in log messages.
- Enable logging in your application's configuration, and adjust log levels as needed for different environments (e.g., development, staging, production).
- Use breakpoints strategically to pause execution and inspect program state during debugging.
- Utilize exception handling and logging together to capture and handle errors effectively.

By combining logging and debugging techniques, you can efficiently diagnose issues, understand application behavior, and maintain code quality in your .NET Core C# applications. Let me know if you need further clarification or more examples!