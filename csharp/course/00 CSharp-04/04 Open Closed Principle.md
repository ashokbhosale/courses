**Definition and Purpose of OCP:**

The Open/Closed Principle (OCP) is another fundamental principle of object-oriented design. It states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, the behavior of a module should be extendable without modifying its source code.

The purpose of OCP is to encourage software designs that are resilient to change. By adhering to OCP, we can add new functionality or behaviors to existing code without altering its structure or behavior, thereby reducing the risk of introducing bugs and maintaining code integrity.

**Applying OCP in C#:**

**Designing Classes and Interfaces for Extension:**

To apply OCP, we design classes and interfaces in a way that allows them to be extended without modification. We achieve this by defining clear interfaces and leveraging inheritance and polymorphism.

**Using Inheritance and Polymorphism:**

We can use inheritance to create a base class or interface that defines the common behavior, and then create subclasses that extend or override this behavior as needed. Polymorphism allows us to treat objects of different subclasses uniformly based on their common base class or interface.

**Design Patterns Supporting OCP:**

Design patterns like Strategy and Decorator are commonly used to support OCP by enabling flexible extension of functionality without modifying existing code.

Let's illustrate OCP with an example in .NET Core C#:

```csharp
using System;

// Abstract base class or interface defining the common behavior
public interface IShape
{
    double Area();
}

// Concrete implementation of the base class or interface
public class Rectangle : IShape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public double Area()
    {
        return Width * Height;
    }
}

// Another concrete implementation of the base class or interface
public class Circle : IShape
{
    public double Radius { get; set; }

    public double Area()
    {
        return Math.PI * Math.Pow(Radius, 2);
    }
}

// Client code that uses the interface without modification
public class AreaCalculator
{
    public double CalculateTotalArea(IShape[] shapes)
    {
        double totalArea = 0;
        foreach (var shape in shapes)
        {
            totalArea += shape.Area();
        }
        return totalArea;
    }
}
```

In this example, the `IShape` interface defines the common behavior for calculating the area of different shapes. The `Rectangle` and `Circle` classes implement this interface and provide their own implementation of the `Area()` method. The `AreaCalculator` class uses polymorphism to calculate the total area of a collection of shapes without needing to know the specific implementation details of each shape.

**Design Patterns Supporting OCP:**

Let's extend our example to demonstrate how the Strategy pattern can support OCP:

```csharp
// Strategy pattern interface
public interface IAreaCalculatorStrategy
{
    double CalculateArea();
}

// Strategy pattern implementations
public class RectangleAreaCalculatorStrategy : IAreaCalculatorStrategy
{
    private readonly Rectangle _rectangle;

    public RectangleAreaCalculatorStrategy(Rectangle rectangle)
    {
        _rectangle = rectangle;
    }

    public double CalculateArea()
    {
        return _rectangle.Width * _rectangle.Height;
    }
}

public class CircleAreaCalculatorStrategy : IAreaCalculatorStrategy
{
    private readonly Circle _circle;

    public CircleAreaCalculatorStrategy(Circle circle)
    {
        _circle = circle;
    }

    public double CalculateArea()
    {
        return Math.PI * Math.Pow(_circle.Radius, 2);
    }
}
```

In this extended example, the Strategy pattern allows us to encapsulate the calculation of area for each shape into separate strategy classes. This makes it easy to add new shapes without modifying existing code, thus adhering to OCP.