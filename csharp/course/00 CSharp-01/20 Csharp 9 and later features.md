C# 9 introduced several new features and enhancements to the language, offering developers more expressive power, increased productivity, and improved safety. Here's an overview of some of the notable features introduced in C# 9 and later versions, including their compatibility with .NET Core:

### Records

Records provide a concise syntax for defining immutable data types. They are particularly useful for representing data transfer objects (DTOs), entities, and other types where immutability and value semantics are desired.

```csharp
public record Person(string FirstName, string LastName);
```

### Init-only Properties

Init-only properties allow you to create properties that can only be set during object initialization, but not afterwards. This helps enforce immutability while retaining object initialization syntax.

```csharp
public class Point
{
    public int X { get; init; }
    public int Y { get; init; }
}
```

### Top-level Statements

Top-level statements enable you to write simple console applications and scripts without the need for a `Main` method or wrapping code in a class.

```csharp
using System;

Console.WriteLine("Hello, World!");
```

### Pattern Matching Enhancements

Pattern matching enhancements include improvements to switch expressions, relational patterns, and logical patterns, making pattern matching more powerful and expressive.

```csharp
public static decimal ComputeSalesTax(object country) => country switch
{
    "USA" => 0.07m,
    "UK" => 0.20m,
    _ => throw new ArgumentException("Unknown country", nameof(country))
};
```

### Target-typed `new` Expressions

Target-typed `new` expressions allow you to omit the type name when creating instances, improving code readability and reducing redundancy.

```csharp
List<string> names = new();
```

### Covariant Returns

Covariant returns enable overriding methods to return more derived types than those declared in the base class, providing more flexibility in class hierarchies.

```csharp
public abstract class Animal
{
    public abstract Animal Reproduce();
}

public class Dog : Animal
{
    public override Dog Reproduce() => new Dog();
}
```

### Records Semantics

Records semantics include with-expressions, copy semantics, equality members, and deconstruction support, enhancing the usability and expressiveness of records.

```csharp
public record Person(string FirstName, string LastName);

var person1 = new Person("John", "Doe");
var person2 = person1 with { LastName = "Smith" };
```

These are some of the key features introduced in C# 9 and later versions. They are compatible with .NET Core, allowing you to leverage the latest language enhancements in your .NET Core applications. Let me know if you need further clarification or more examples!