**Advanced C# Features:**

**Delegates, Events, and Lambda Expressions:**

Delegates are type-safe function pointers that allow you to pass methods as parameters to other methods or store them as data. Events are a special type of delegate used to implement the observer pattern, allowing objects to subscribe to and receive notifications about changes or actions.

```csharp
// Example of delegate and event
public delegate void EventHandler(string message);

public class Publisher
{
    public event EventHandler Notify;

    public void DoSomething()
    {
        // Do something
        Notify?.Invoke("Something happened!");
    }
}

public class Subscriber
{
    public void HandleEvent(string message)
    {
        Console.WriteLine($"Event handled: {message}");
    }
}

// Usage
var publisher = new Publisher();
var subscriber = new Subscriber();

publisher.Notify += subscriber.HandleEvent;
publisher.DoSomething(); // This will trigger the event and the subscriber's HandleEvent method will be called
```

Lambda expressions are concise, inline functions that can be used to define delegates or expression trees. They provide a more readable and compact syntax for defining anonymous methods.

```csharp
// Example of lambda expression
Func<int, int, int> add = (x, y) => x + y;
Console.WriteLine(add(3, 5)); // Output: 8
```

**Asynchronous Programming with async/await:**

Async/await is a feature introduced in C# to simplify asynchronous programming. It allows you to write asynchronous code that looks synchronous, making it easier to understand and maintain.

```csharp
// Example of async/await
public async Task<string> FetchDataAsync()
{
    var httpClient = new HttpClient();
    var response = await httpClient.GetAsync("https://api.example.com/data");
    return await response.Content.ReadAsStringAsync();
}
```

**Generics and Collections:**

Generics allow you to create classes, interfaces, and methods that work with any data type. They provide type safety and code reusability.

```csharp
// Example of generics
public class Stack<T>
{
    private List<T> items = new List<T>();

    public void Push(T item)
    {
        items.Add(item);
    }

    public T Pop()
    {
        var item = items.Last();
        items.Remove(item);
        return item;
    }
}
```

**Attributes and Reflection:**

Attributes are metadata that provide additional information about types, methods, properties, or parameters. Reflection allows you to inspect and manipulate types, members, and metadata at runtime.

```csharp
// Example of attribute and reflection
[Serializable]
public class MyClass
{
    public string Name { get; set; }
}

// Usage of reflection to get attributes
var type = typeof(MyClass);
var attributes = type.GetCustomAttributes();
foreach (var attribute in attributes)
{
    Console.WriteLine(attribute.GetType().Name);
}
```

These are some advanced features of C# that are commonly used in .NET Core applications. Understanding and mastering these features can help you write more efficient and maintainable code.