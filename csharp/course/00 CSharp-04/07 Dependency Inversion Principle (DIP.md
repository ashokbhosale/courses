**Definition and Purpose of DIP:**

The Dependency Inversion Principle (DIP) is a principle in object-oriented design that states high-level modules should not depend on low-level modules. Instead, both should depend on abstractions. This principle emphasizes decoupling between components and promoting the use of abstractions to achieve flexibility and maintainability.

The purpose of DIP is to reduce dependencies between classes/modules, making the system more flexible, extensible, and easier to maintain. By depending on abstractions rather than concrete implementations, DIP enables easier testing, swapping of components, and overall better software design.

**Applying DIP in C#:**

**Writing Code that Depends on Abstractions, not Concretions:**

To apply DIP, we design our code to depend on interfaces or abstract classes rather than concrete implementations. This allows for easier substitution of components and reduces coupling between modules.

**Using Dependency Injection to Achieve Loose Coupling:**

Dependency Injection (DI) is a common technique used to implement DIP in practice. It involves injecting dependencies into a class rather than creating them within the class itself. This allows dependencies to be easily replaced or mocked, promoting loose coupling and adherence to DIP.

**Design Patterns that Support DIP:**

Several design patterns support DIP by facilitating the use of abstractions and dependency injection. Patterns such as Dependency Injection and Factory Method promote the use of abstractions and loose coupling between components.

**Example in .NET Core C#:**

Let's consider an example involving a logger interface and a high-level class that depends on it:

```csharp
using System;

// Logger interface
public interface ILogger
{
    void Log(string message);
}

// Concrete implementation of the logger interface
public class FileLogger : ILogger
{
    public void Log(string message)
    {
        // Log message to a file
        Console.WriteLine($"Logging to file: {message}");
    }
}

// High-level class that depends on the logger interface
public class DataProcessor
{
    private readonly ILogger _logger;

    public DataProcessor(ILogger logger)
    {
        _logger = logger;
    }

    public void ProcessData(string data)
    {
        // Process data
        _logger.Log("Data processed successfully");
    }
}
```

In this example, the `DataProcessor` class depends on the `ILogger` interface rather than a specific logger implementation. This adheres to DIP by depending on abstractions instead of concrete implementations.

**Using Dependency Injection to Achieve Loose Coupling:**

We can use dependency injection to inject the logger implementation into the `DataProcessor` class:

```csharp
// Dependency injection configuration
class Program
{
    static void Main(string[] args)
    {
        // Setup dependency injection container
        var serviceProvider = new ServiceCollection()
            .AddSingleton<ILogger, FileLogger>()
            .BuildServiceProvider();

        // Resolve the DataProcessor with injected logger
        var dataProcessor = serviceProvider.GetRequiredService<DataProcessor>();

        // Use the data processor
        dataProcessor.ProcessData("Sample data");
    }
}
```

By configuring the dependency injection container to provide an instance of `FileLogger` when `ILogger` is requested, we achieve loose coupling between `DataProcessor` and the logger implementation, adhering to DIP.

**Design Patterns Supporting DIP:**

The Dependency Injection pattern is a prime example of a design pattern that supports DIP by facilitating the injection of dependencies into classes. Similarly, the Factory Method pattern allows for the creation of objects without specifying their concrete classes, promoting the use of abstractions and adherence to DIP.