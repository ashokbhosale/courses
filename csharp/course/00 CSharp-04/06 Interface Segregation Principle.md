**Definition and Purpose of ISP:**

The Interface Segregation Principle (ISP) is one of the SOLID principles in object-oriented design. It states that clients should not be forced to depend on interfaces they do not use. In other words, interfaces should be specific to clients' needs, and they should not contain unnecessary methods that clients don't require.

The purpose of ISP is to promote cohesion and prevent coupling in software systems. By designing interfaces that are focused and tailored to specific client requirements, we can improve code maintainability, flexibility, and scalability.

**Applying ISP in C#:**

**Designing Cohesive and Focused Interfaces:**

To apply ISP effectively, it's essential to design interfaces that are cohesive and focused on specific client needs. Interfaces should contain methods that are logically related and necessary for the functionality required by clients.

**Breaking Down Large Interfaces into Smaller Ones:**

If an interface becomes too large or contains methods that are not relevant to all clients, it's advisable to break it down into smaller, more focused interfaces. This allows clients to implement only the interfaces they need, reducing unnecessary dependencies and promoting adherence to ISP.

**Design Patterns that Support ISP:**

Several design patterns support ISP by facilitating the design of interfaces that adhere to the principle. Patterns such as Adapter and Facade help in providing tailored interfaces to clients while hiding unnecessary complexity.

**Example in .NET Core C#:**

Let's consider an example involving a document management system:

```csharp
using System;

// Large interface with multiple methods
public interface IDocumentManager
{
    void CreateDocument();
    void OpenDocument();
    void SaveDocument();
    void PrintDocument();
}

// Client class that only needs to create and save documents
public class DocumentClient
{
    private readonly IDocumentManager _documentManager;

    public DocumentClient(IDocumentManager documentManager)
    {
        _documentManager = documentManager;
    }

    public void CreateAndSaveDocument()
    {
        _documentManager.CreateDocument();
        _documentManager.SaveDocument();
    }
}

// Another client class that only needs to open documents
public class DocumentViewer
{
    private readonly IDocumentManager _documentManager;

    public DocumentViewer(IDocumentManager documentManager)
    {
        _documentManager = documentManager;
    }

    public void OpenDocument()
    {
        _documentManager.OpenDocument();
    }
}
```

In this example, the `IDocumentManager` interface violates ISP because it contains methods that are not relevant to all clients. Instead, we can break it down into smaller interfaces:

```csharp
// Smaller interfaces tailored to specific client needs
public interface ICreateDocument
{
    void CreateDocument();
}

public interface IOpenDocument
{
    void OpenDocument();
}

public interface ISaveDocument
{
    void SaveDocument();
}
```

Now, clients can implement only the interfaces they need, adhering to ISP. For example:

```csharp
public class DocumentClient : ICreateDocument, ISaveDocument
{
    // Implementation for CreateDocument and SaveDocument
}

public class DocumentViewer : IOpenDocument
{
    // Implementation for OpenDocument
}
```

**Design Patterns Supporting ISP:**

Let's demonstrate how the Adapter pattern supports ISP:

```csharp
// Interface tailored to a specific client's needs
public interface ITarget
{
    void MethodA();
}

// Adaptee interface with methods that may not be relevant to all clients
public interface IAdaptee
{
    void MethodB();
    void MethodC();
}

// Adapter class that adapts the Adaptee interface to the Target interface
public class Adapter : ITarget
{
    private readonly IAdaptee _adaptee;

    public Adapter(IAdaptee adaptee)
    {
        _adaptee = adaptee;
    }

    public void MethodA()
    {
        // Implementation for MethodA using methods from IAdaptee
        _adaptee.MethodB();
        _adaptee.MethodC();
    }
}
```

In this example, the Adapter pattern allows us to provide a tailored interface (`ITarget`) to the client while encapsulating the complexity of the Adaptee interface (`IAdaptee`). This promotes adherence to ISP by providing specific interfaces to clients without exposing unnecessary methods.