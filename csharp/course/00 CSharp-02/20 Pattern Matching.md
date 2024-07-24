Pattern matching in C# is a powerful feature introduced in C# 7.0 and improved upon in subsequent versions, including .NET Core. It allows you to write more concise and readable code by enabling you to match values against patterns and execute code based on the match.

Here's a brief overview of how pattern matching works in .NET Core C#:

1. **Type Pattern Matching**: You can use the `is` keyword to check if an object is of a certain type and optionally cast it to that type in the same operation. For example:

```csharp
object obj = "Hello";
if (obj is string str)
{
    // Here, str is now of type string
    Console.WriteLine(str.ToUpper());
}
```

2. **Switch Statement with Patterns**: The `switch` statement in C# supports patterns since C# 7.0. You can match against various patterns including type patterns, constant patterns, var patterns, and more. For example:

```csharp
object obj = "Hello";
switch (obj)
{
    case string str:
        Console.WriteLine(str.ToUpper());
        break;
    case int i when i > 0:
        Console.WriteLine("Positive integer");
        break;
    case int i:
        Console.WriteLine("Non-positive integer");
        break;
    default:
        Console.WriteLine("Unknown type");
        break;
}
```

3. **Property Patterns**: You can use properties of objects in patterns to match against specific values. For example:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }
}

Point point = new Point { X = 1, Y = 2 };
switch (point)
{
    case Point { X: 0, Y: 0 }:
        Console.WriteLine("Origin");
        break;
    case Point { X: var x, Y: var y }:
        Console.WriteLine($"({x}, {y})");
        break;
}
```

4. **Tuple Patterns**: You can use tuple patterns to deconstruct tuples and match against their elements. For example:

```csharp
(object, object) pair = (1, "two");
switch (pair)
{
    case (int, string) p:
        Console.WriteLine($"Int: {p.Item1}, String: {p.Item2}");
        break;
    case (string, int) p:
        Console.WriteLine($"String: {p.Item1}, Int: {p.Item2}");
        break;
}
```

These are just a few examples of pattern matching capabilities in C#. Pattern matching can significantly enhance readability and maintainability of your code, especially when dealing with complex data structures and conditions.