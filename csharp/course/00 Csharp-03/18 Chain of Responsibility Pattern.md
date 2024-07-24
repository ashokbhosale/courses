### Chain of Responsibility Pattern

#### Intent and Motivation:
The Chain of Responsibility pattern is a behavioral design pattern that allows multiple objects to handle a request without explicitly specifying the receiver. It creates a chain of objects, each of which has a chance to process the request or pass it on to the next object in the chain. The main intent of the Chain of Responsibility pattern is to decouple senders and receivers of requests, allowing them to be composed dynamically at runtime.

The motivation behind the Chain of Responsibility pattern is to avoid coupling the sender of a request to its receiver, providing flexibility in handling requests and enabling dynamic composition of handlers. By organizing handlers into a chain, the pattern promotes loose coupling and separation of concerns, allowing each handler to focus on a specific aspect of request processing.

#### Handling Requests Dynamically:
In the Chain of Responsibility pattern, there are two main participants:

- **Handler**: Represents an object that can handle a request or pass it on to the next handler in the chain. It defines a common interface for handling requests and maintaining a reference to the next handler in the chain.

- **Concrete Handler**: Implements the handler interface and defines how to handle a request. It checks whether it can handle the request and either processes it or forwards it to the next handler in the chain.

#### Implementation Techniques:
The Chain of Responsibility pattern can be implemented using the following techniques:

1. **Handler Interface or Base Class**: Define a handler interface or base class that declares a method for handling requests and maintaining a reference to the next handler in the chain.

2. **Concrete Handlers**: Implement concrete handler classes that inherit from the handler interface or base class. Each concrete handler class represents a specific handler in the chain and defines how to handle a request.

3. **Chain Construction**: Construct the chain of handlers by linking them together in a sequence. Handlers can be added to the chain dynamically at runtime.

#### Use Cases and Examples with .NET Core C#:
The Chain of Responsibility pattern is commonly used in scenarios where you need to handle requests dynamically and decouple the sender of a request from its receiver, such as:

- **Event Handling**: Processing events or messages in a system, where multiple components may be interested in handling the same event or message.
  
- **Middleware Processing**: Implementing middleware pipelines in web applications, where each middleware component can process a request or pass it on to the next middleware in the pipeline.
  
- **Exception Handling**: Handling exceptions in an application, where different handlers may be responsible for handling specific types of exceptions or errors.

Example:
```csharp
using System;

// Handler interface
public interface IHandler
{
    void HandleRequest(int request);
}

// Base handler
public abstract class BaseHandler : IHandler
{
    private IHandler _nextHandler;

    public void SetNextHandler(IHandler nextHandler)
    {
        _nextHandler = nextHandler;
    }

    public void HandleRequest(int request)
    {
        if (CanHandleRequest(request))
        {
            ProcessRequest(request);
        }
        else if (_nextHandler != null)
        {
            _nextHandler.HandleRequest(request);
        }
        else
        {
            Console.WriteLine("No handler available");
        }
    }

    protected abstract bool CanHandleRequest(int request);
    protected abstract void ProcessRequest(int request);
}

// Concrete handler: Handler for requests less than 10
public class Handler1 : BaseHandler
{
    protected override bool CanHandleRequest(int request)
    {
        return request < 10;
    }

    protected override void ProcessRequest(int request)
    {
        Console.WriteLine($"Handler1: Handling request {request}");
    }
}

// Concrete handler: Handler for requests between 10 and 20
public class Handler2 : BaseHandler
{
    protected override bool CanHandleRequest(int request)
    {
        return request >= 10 && request < 20;
    }

    protected override void ProcessRequest(int request)
    {
        Console.WriteLine($"Handler2: Handling request {request}");
    }
}

// Concrete handler: Handler for requests greater than or equal to 20
public class Handler3 : BaseHandler
{
    protected override bool CanHandleRequest(int request)
    {
        return request >= 20;
    }

    protected override void ProcessRequest(int request)
    {
        Console.WriteLine($"Handler3: Handling request {request}");
    }
}

// Client code
public class Client
{
    public void Main()
    {
        // Create chain of handlers
        var handler1 = new Handler1();
        var handler2 = new Handler2();
        var handler3 = new Handler3();

        handler1.SetNextHandler(handler2);
        handler2.SetNextHandler(handler3);

        // Process requests
        handler1.HandleRequest(5);
        handler1.HandleRequest(15);
        handler1.HandleRequest(25);
    }
}

// Usage
public class Program
{
    public static void Main()
    {
        var client = new Client();
        client.Main();
    }
}
```

In this example, the Chain of Responsibility pattern is used to create a chain of handlers (`Handler1`, `Handler2`, `Handler3`) that handle requests based on their range. Each handler checks whether it can handle the request and either processes it or passes it on to the next handler in the chain. The client code creates the chain of handlers and initiates requests, allowing requests to be handled dynamically based on their range.