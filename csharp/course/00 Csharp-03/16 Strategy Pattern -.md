### Strategy Pattern

#### Intent and Motivation:
The Strategy pattern is a behavioral design pattern that defines a family of algorithms, encapsulates each one, and makes them interchangeable. It enables clients to vary algorithms or behaviors independently from the context that uses them. The main intent of the Strategy pattern is to define a set of algorithms or behaviors, encapsulate each one as a separate class, and allow clients to choose the appropriate algorithm dynamically at runtime.

The motivation behind the Strategy pattern is to promote code reuse, flexibility, and maintainability by separating the behavior from the context that uses it. By encapsulating algorithms or behaviors as separate classes, the Strategy pattern allows them to be developed, tested, and modified independently. Clients can select the desired strategy dynamically based on changing requirements or conditions without modifying the context.

#### Encapsulating Algorithms and Behaviors:
In the Strategy pattern, there are three main participants:

- **Context**: Represents the object that uses a strategy. It maintains a reference to a strategy object and delegates the execution of a particular algorithm or behavior to it.

- **Strategy**: Defines an interface or abstract class that represents a family of algorithms or behaviors. It declares a method or set of methods that encapsulate the algorithm or behavior.

- **Concrete Strategy**: Implements a specific algorithm or behavior defined by the strategy interface. It provides the actual implementation for the algorithm or behavior.

#### Implementation Techniques:
The Strategy pattern can be implemented using the following techniques:

1. **Strategy Interface or Base Class**: Define a strategy interface or base class that declares a method for performing the algorithm or behavior.

2. **Concrete Strategies**: Implement concrete strategy classes that inherit from the strategy interface or base class. Each concrete strategy class provides a different implementation of the algorithm or behavior.

3. **Context**: Define a context class that maintains a reference to a strategy object and delegates the execution of the algorithm or behavior to it. The context class may provide methods for setting or changing the strategy dynamically.

#### Use Cases and Examples with .NET Core C#:
The Strategy pattern is commonly used in scenarios where you need to encapsulate and interchange algorithms or behaviors dynamically, such as:

- **Sorting Algorithms**: Providing different sorting algorithms (e.g., quicksort, mergesort) to sort collections of data based on various criteria or performance requirements.
  
- **Compression Algorithms**: Offering different compression algorithms (e.g., gzip, deflate) to compress or decompress files based on their types or sizes.
  
- **Payment Processing**: Supporting different payment processing strategies (e.g., credit card, PayPal) for handling transactions in an e-commerce application.

Example:
```csharp
using System;

// Strategy interface
public interface ISortStrategy
{
    void Sort(int[] data);
}

// Concrete strategy: Bubble sort
public class BubbleSortStrategy : ISortStrategy
{
    public void Sort(int[] data)
    {
        Console.WriteLine("Bubble sort");
        // Bubble sort implementation
    }
}

// Concrete strategy: Quick sort
public class QuickSortStrategy : ISortStrategy
{
    public void Sort(int[] data)
    {
        Console.WriteLine("Quick sort");
        // Quick sort implementation
    }
}

// Context
public class SortContext
{
    private readonly ISortStrategy _strategy;

    public SortContext(ISortStrategy strategy)
    {
        _strategy = strategy;
    }

    public void Sort(int[] data)
    {
        _strategy.Sort(data);
    }
}

// Client code
public class Client
{
    public void Main()
    {
        var data = new int[] { 5, 2, 7, 3, 9, 1 };

        // Use bubble sort strategy
        var bubbleSortStrategy = new BubbleSortStrategy();
        var sortContext = new SortContext(bubbleSortStrategy);
        sortContext.Sort(data);

        // Use quick sort strategy
        var quickSortStrategy = new QuickSortStrategy();
        sortContext = new SortContext(quickSortStrategy);
        sortContext.Sort(data);
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

In this example, the Strategy pattern is used to encapsulate sorting algorithms (`BubbleSortStrategy` and `QuickSortStrategy`) as separate classes that implement the `ISortStrategy` interface. The `SortContext` class acts as the context that uses a strategy and delegates sorting operations to it. The client code creates instances of concrete strategies and passes them to the context dynamically, allowing different sorting algorithms to be used interchangeably.