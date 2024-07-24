Certainly! Design patterns are reusable solutions to common problems that occur during software development. Here are some common design patterns implemented in C# .NET Core:

### 1. Factory Method Pattern

The Factory Method Pattern defines an interface for creating an object, but allows subclasses to alter the type of objects that will be created.

```csharp
public interface IProduct
{
    void Operation();
}

public class ConcreteProductA : IProduct
{
    public void Operation()
    {
        Console.WriteLine("ConcreteProductA operation.");
    }
}

public class ConcreteProductB : IProduct
{
    public void Operation()
    {
        Console.WriteLine("ConcreteProductB operation.");
    }
}

public interface IFactory
{
    IProduct CreateProduct();
}

public class ConcreteFactoryA : IFactory
{
    public IProduct CreateProduct()
    {
        return new ConcreteProductA();
    }
}

public class ConcreteFactoryB : IFactory
{
    public IProduct CreateProduct()
    {
        return new ConcreteProductB();
    }
}
```

### 2. Singleton Pattern

The Singleton Pattern ensures that a class has only one instance and provides a global point of access to that instance.

```csharp
public class Singleton
{
    private static Singleton _instance;
    private Singleton() { }

    public static Singleton Instance
    {
        get
        {
            if (_instance == null)
            {
                _instance = new Singleton();
            }
            return _instance;
        }
    }
}
```

### 3. Strategy Pattern

The Strategy Pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. It lets the algorithm vary independently from clients that use it.

```csharp
public interface IStrategy
{
    void Algorithm();
}

public class ConcreteStrategyA : IStrategy
{
    public void Algorithm()
    {
        Console.WriteLine("Using strategy A.");
    }
}

public class ConcreteStrategyB : IStrategy
{
    public void Algorithm()
    {
        Console.WriteLine("Using strategy B.");
    }
}

public class Context
{
    private readonly IStrategy _strategy;

    public Context(IStrategy strategy)
    {
        _strategy = strategy;
    }

    public void ExecuteStrategy()
    {
        _strategy.Algorithm();
    }
}
```

### 4. Observer Pattern

The Observer Pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

```csharp
public interface IObserver
{
    void Update(string message);
}

public interface ISubject
{
    void Attach(IObserver observer);
    void Detach(IObserver observer);
    void Notify(string message);
}

public class ConcreteSubject : ISubject
{
    private List<IObserver> _observers = new List<IObserver>();

    public void Attach(IObserver observer)
    {
        _observers.Add(observer);
    }

    public void Detach(IObserver observer)
    {
        _observers.Remove(observer);
    }

    public void Notify(string message)
    {
        foreach (var observer in _observers)
        {
            observer.Update(message);
        }
    }
}

public class ConcreteObserver : IObserver
{
    public void Update(string message)
    {
        Console.WriteLine($"Received message: {message}");
    }
}
```

These are just a few examples of common design patterns implemented in C# .NET Core. Design patterns help improve code maintainability, extensibility, and flexibility by providing well-established solutions to recurring problems. Let me know if you need further clarification or more examples!