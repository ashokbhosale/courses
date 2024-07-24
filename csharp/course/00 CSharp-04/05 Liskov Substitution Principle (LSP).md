**Definition and Purpose of LSP:**

The Liskov Substitution Principle (LSP) is a fundamental principle in object-oriented programming that ensures that objects of a superclass should be substitutable with objects of its subclasses without altering the correctness of the program. In other words, derived classes must be usable through the interface of their base classes without causing unexpected behavior or violating any invariants.

The purpose of LSP is to maintain the consistency and correctness of object-oriented designs, allowing for polymorphic substitution and promoting the reuse of code.

**Applying LSP in C#:**

**Writing Code that Respects Contracts:**

To apply LSP effectively, it's essential to define and adhere to contracts. Contracts specify the behavior and constraints that must be upheld by both base and derived classes. These contracts can be enforced through interfaces, abstract classes, or documentation.

**Using Interfaces and Abstract Classes Effectively:**

Interfaces and abstract classes are powerful tools for implementing LSP in C#. They allow you to define contracts that derived classes must adhere to while providing flexibility in implementation.

**Design Patterns that Support LSP:**

Several design patterns support LSP by facilitating the design of hierarchies of classes that adhere to the principle. Patterns such as Template Method and Factory Method promote polymorphism and enable the substitution of objects without altering the behavior of the system.

**Example in .NET Core C#:**

Let's consider an example involving geometric shapes:

```csharp
using System;

// Base class representing a geometric shape
public abstract class Shape
{
    public abstract double Area();
}

// Derived class representing a rectangle
public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double Area()
    {
        return Width * Height;
    }
}

// Derived class representing a square
public class Square : Shape
{
    public double Side { get; set; }

    public override double Area()
    {
        return Math.Pow(Side, 2);
    }
}

// Client code using the Shape interface
public class ShapeManager
{
    public void PrintArea(Shape shape)
    {
        Console.WriteLine($"Area: {shape.Area()}");
    }
}
```

In this example, both `Rectangle` and `Square` inherit from the `Shape` base class and provide their implementations of the `Area()` method. Despite the differences in behavior between rectangles and squares, they can be seamlessly substituted for each other in the `ShapeManager` class without affecting the correctness of the program, adhering to LSP.

**Design Patterns Supporting LSP:**

Let's demonstrate how the Template Method pattern supports LSP:

```csharp
// Template Method pattern
public abstract class DocumentProcessor
{
    public void ProcessDocument()
    {
        OpenDocument();
        ReadDocument();
        CloseDocument();
    }

    protected abstract void OpenDocument();
    protected abstract void ReadDocument();
    protected abstract void CloseDocument();
}

// Concrete class implementing the DocumentProcessor
public class PDFProcessor : DocumentProcessor
{
    protected override void OpenDocument()
    {
        Console.WriteLine("Opening PDF document...");
    }

    protected override void ReadDocument()
    {
        Console.WriteLine("Reading PDF document...");
    }

    protected override void CloseDocument()
    {
        Console.WriteLine("Closing PDF document...");
    }
}
```

In this example, any derived class of `DocumentProcessor` can override the template methods to implement specific document processing behaviors while adhering to the contract established by the base class. This promotes substitutability and ensures adherence to LSP.