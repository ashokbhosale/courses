

### Proxy Pattern

#### Intent and Motivation:
The Proxy pattern is a structural design pattern that provides a surrogate or placeholder for another object to control access to it. It acts as an intermediary or wrapper around the real object, allowing you to add extra functionality or control access to the object without changing its interface. The main intent of the Proxy pattern is to provide a level of indirection and control over access to objects, enabling additional behavior to be added transparently.

The motivation behind the Proxy pattern is to provide a way to control access to objects or manage their creation and destruction, especially when dealing with expensive or remote resources. Proxies can be used to defer the creation of objects until they are actually needed, limit access to sensitive or restricted operations, cache results to improve performance, or provide a simplified interface to complex subsystems.

#### Virtual Proxy, Protection Proxy, and Remote Proxy:
The Proxy pattern can be implemented in various forms to address different concerns:

- **Virtual Proxy**: Defers the creation of an expensive object until it is actually needed, allowing lazy initialization. It acts as a placeholder for the real object, which is created only when a client requests it.
  
- **Protection Proxy**: Controls access to the real object by checking permissions or credentials before allowing operations to be performed. It acts as a gatekeeper, enforcing security policies to restrict unauthorized access.
  
- **Remote Proxy**: Provides a local representation of a remote object to interact with it transparently. It acts as a client-side proxy for accessing remote services or resources, hiding the complexity of network communication.

#### Implementation Techniques:
The Proxy pattern can be implemented using the following techniques:

1. **Common Interface or Base Class**: Define a common interface or base class that represents both the real subject and its proxy. This allows clients to interact with the proxy in the same way as with the real subject.

2. **Lazy Initialization**: Use lazy initialization to defer the creation of the real subject until it is actually needed. This can be achieved by instantiating the real subject lazily when a client requests it for the first time.

3. **Access Control**: Implement access control mechanisms in the proxy to restrict or control access to the real subject. This can involve checking permissions, credentials, or other security-related information before allowing operations to proceed.

4. **Network Communication**: Implement network communication logic in the proxy to facilitate interaction with remote objects or services. This can involve marshaling method calls, handling network protocols, and managing communication channels.

#### Use Cases and Examples with .NET Core C#:
The Proxy pattern is commonly used in scenarios where you need to control access to objects, manage their creation and destruction, or facilitate interaction with remote resources. Some common use cases and examples in .NET Core C# include:

- **Lazy Initialization**: Deferring the creation of expensive objects or resources until they are actually needed, to improve performance and resource utilization.
  
- **Access Control and Security**: Enforcing access control policies to restrict or manage access to sensitive or restricted operations, such as authentication, authorization, and auditing.
  
- **Remote Communication**: Facilitating communication with remote services or resources by providing local proxies that handle network communication transparently.

Example:
```csharp
using System;

// Subject interface
public interface ISubject
{
    void Request();
}

// Real subject class
public class RealSubject : ISubject
{
    public void Request()
    {
        Console.WriteLine("RealSubject: Handling request");
    }
}

// Proxy class
public class Proxy : ISubject
{
    private RealSubject _realSubject;

    public void Request()
    {
        // Lazy initialization: create the real subject when needed
        if (_realSubject == null)
        {
            _realSubject = new RealSubject();
        }

        // Forward the request to the real subject
        _realSubject.Request();
    }
}

// Client code
public class Client
{
    public void Run(ISubject subject)
    {
        subject.Request();
    }
}

// Usage
public class Program
{
    public static void Main()
    {
        // Create a proxy object
        var proxy = new Proxy();

        // Execute the request through the proxy
        var client = new Client();
        client.Run(proxy);
    }
}
```

In this example, the Proxy pattern is used to control access to the `RealSubject` object by providing a `Proxy` object that acts as a placeholder. The proxy defers the creation of the real subject until it is actually needed (lazy initialization), and then forwards requests to the real subject transparently. The client code interacts with the proxy in the same way as with the real subject, allowing additional functionality or access control to be added transparently.