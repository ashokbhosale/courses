The SOLID principles are a set of five design principles that aim to make software designs more understandable, flexible, and maintainable. These principles provide guidelines for writing clean, modular, and maintainable code. Let's go through each of the SOLID principles and see how they apply in C# .NET Core:

### 1. Single Responsibility Principle (SRP)

The SRP states that a class should have only one reason to change, meaning it should have only one responsibility.

```csharp
// Bad example
public class User
{
    public void Register() { }
    public void SendEmail() { }
    public void GenerateReport() { }
}

// Good example
public class User
{
    public void Register() { }
}

public class EmailSender
{
    public void SendEmail() { }
}

public class ReportGenerator
{
    public void GenerateReport() { }
}
```

### 2. Open/Closed Principle (OCP)

The OCP states that classes should be open for extension but closed for modification, meaning that you should be able to extend a class's behavior without modifying its source code.

```csharp
// Bad example
public class Rectangle
{
    public double Width { get; set; }
    public double Height { get; set; }
}

// Good example
public abstract class Shape
{
    public abstract double Area();
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double Area()
    {
        return Width * Height;
    }
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double Area()
    {
        return Math.PI * Radius * Radius;
    }
}
```

### 3. Liskov Substitution Principle (LSP)

The LSP states that objects of a superclass should be replaceable with objects of its subclass without affecting the correctness of the program.

```csharp
// Bad example
public class Rectangle
{
    public virtual double Width { get; set; }
    public virtual double Height { get; set; }
}

public class Square : Rectangle
{
    public override double Width
    {
        get => base.Width;
        set { base.Width = value; base.Height = value; }
    }

    public override double Height
    {
        get => base.Height;
        set { base.Height = value; base.Width = value; }
    }
}

// Good example
public abstract class Shape
{
    public abstract double Area();
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double Area()
    {
        return Width * Height;
    }
}

public class Square : Shape
{
    public double Side { get; set; }

    public override double Area()
    {
        return Side * Side;
    }
}
```

### 4. Interface Segregation Principle (ISP)

The ISP states that no client should be forced to depend on methods it does not use, meaning that classes should not be forced to implement interfaces they don't need.

```csharp
// Bad example
public interface IWorker
{
    void Work();
    void TakeBreak();
}

public class Manager : IWorker
{
    public void Work() { }
    public void TakeBreak() { }
}

// Good example
public interface IWorker
{
    void Work();
}

public interface IBreakable
{
    void TakeBreak();
}

public class Manager : IWorker, IBreakable
{
    public void Work() { }
    public void TakeBreak() { }
}
```

### 5. Dependency Inversion Principle (DIP)

The DIP states that high-level modules should not depend on low-level modules, but both should depend on abstractions. Abstractions should not depend on details; details should depend on abstractions.

```csharp
// Bad example
public class DataAccess
{
    public void GetData() { }
}

public class BusinessLogic
{
    private readonly DataAccess _dataAccess;

    public BusinessLogic()
    {
        _dataAccess = new DataAccess();
    }
}

// Good example
public interface IDataAccess
{
    void GetData();
}

public class DataAccess : IDataAccess
{
    public void GetData() { }
}

public class BusinessLogic
{
    private readonly IDataAccess _dataAccess;

    public BusinessLogic(IDataAccess dataAccess)
    {
        _dataAccess = dataAccess;
    }
}
```

By following the SOLID principles, you can create more modular, flexible, and maintainable code in C# .NET Core applications. These principles help improve code quality, facilitate testing, and make it easier to extend and modify your codebase. Let me know if you need further clarification or more examples!