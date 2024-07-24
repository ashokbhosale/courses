### Adapter Pattern

#### Intent and Motivation:
The Adapter pattern is a structural design pattern that allows objects with incompatible interfaces to work together. It acts as a bridge between two incompatible interfaces, converting the interface of a class into another interface that clients expect. The main intent of the Adapter pattern is to enable communication and collaboration between classes with different interfaces, without modifying their existing code.

The motivation behind the Adapter pattern is to resolve interface incompatibility issues and facilitate interoperability between existing classes or components. It allows legacy or third-party code to be integrated seamlessly into new systems, without the need for extensive refactoring or redesign. By providing a standardized interface, the Adapter pattern promotes code reusability, flexibility, and maintainability.

#### Class and Object Adapter Variations:
The Adapter pattern can be implemented in two variations: class adapter and object adapter.

- **Class Adapter**: In the class adapter variation, the adapter class inherits from both the target interface and the adaptee class. It acts as a subclass of the adaptee and adapts its interface to match the target interface. This variation requires multiple inheritance, which may not be supported in all programming languages.
  
- **Object Adapter**: In the object adapter variation, the adapter class contains an instance of the adaptee class and implements the target interface. It delegates requests from the target interface to the adaptee object, adapting its interface as needed. This variation uses composition instead of inheritance, making it more flexible and compatible with languages that do not support multiple inheritance.

#### Implementation Techniques:
The Adapter pattern can be implemented using the following techniques:

1. **Class Adapter Implementation**:
   - Define an adapter class that inherits from both the target interface and the adaptee class.
   - Implement the target interface methods by delegating calls to the corresponding methods of the adaptee class.
   - Use the adapter class to adapt the adaptee's interface to match the target interface.

2. **Object Adapter Implementation**:
   - Define an adapter class that implements the target interface and contains an instance of the adaptee class.
   - Implement the target interface methods by forwarding calls to the corresponding methods of the adaptee object.
   - Use the adapter class to adapt the adaptee's interface to match the target interface.

#### Use Cases and Examples with .NET Core C#:
The Adapter pattern is commonly used in scenarios where existing classes or components have incompatible interfaces and need to be integrated into a new system. Some common use cases and examples in .NET Core C# include:

- **Integration with Legacy Systems**: Adapting legacy components or libraries with outdated interfaces to work with modern systems or frameworks.
- **Third-Party Library Integration**: Integrating third-party libraries or APIs with different interfaces into an existing application, without modifying the client code.
- **Interface Standardization**: Providing a standardized interface for interacting with diverse or heterogeneous components, services, or data sources.

Example:
```csharp
using System;

// Target interface
public interface ITarget
{
    void Request();
}

// Adaptee class with incompatible interface
public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("Adaptee's specific request");
    }
}

// Class adapter implementation
public class ClassAdapter : Adaptee, ITarget
{
    public void Request()
    {
        SpecificRequest(); // Calling adaptee's method
    }
}

// Object adapter implementation
public class ObjectAdapter : ITarget
{
    private readonly Adaptee _adaptee;

    public ObjectAdapter(Adaptee adaptee)
    {
        _adaptee = adaptee;
    }

    public void Request()
    {
        _adaptee.SpecificRequest(); // Calling adaptee's method
    }
}

// Client code
public class Client
{
    public void Run(ITarget target)
    {
        target.Request();
    }
}

// Usage
public class Program
{
    public static void Main()
    {
        // Using class adapter
        var classAdapter = new ClassAdapter();
        var client1 = new Client();
        client1.Run(classAdapter); // Output: Adaptee's specific request

        // Using object adapter
        var adaptee = new Adaptee();
        var objectAdapter = new ObjectAdapter(adaptee);
        var client2 = new Client();
        client2.Run(objectAdapter); // Output: Adaptee's specific request
    }
}
```

In this example, the Adapter pattern is used to adapt the interface of the `Adaptee` class to match the `ITarget` interface. Both class adapter (`ClassAdapter`) and object adapter (`ObjectAdapter`) implementations are provided. The client code (`Client`) remains unaware of the underlying interface compatibility, allowing the adaptee's specific request to be invoked seamlessly through the adapter.