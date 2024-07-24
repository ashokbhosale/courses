Lambda expressions are a concise way to represent anonymous methods or functions in C# .NET Core. They provide a compact syntax for defining inline delegate functions without explicitly declaring a separate method. Lambda expressions are commonly used with LINQ queries, event handlers, and functional programming techniques. Here's an overview of lambda expressions in C# .NET Core:

1. **Syntax**:
   - Lambda expressions consist of three main parts: the parameter list, the lambda operator (`=>`), and the body.
   - The parameter list can be empty or contain one or more parameters enclosed in parentheses.
   - The body can be a single statement or a block of statements enclosed in curly braces `{ }`.
   - If the body consists of a single expression, it's implicitly returned; otherwise, you need to use the `return` keyword.

Example of a simple lambda expression:

```csharp
Func<int, int, int> add = (x, y) => x + y;
```

2. **Delegate Types**:
   - Lambda expressions are often used with delegate types such as `Action`, `Func`, and custom delegate types.
   - The delegate type determines the number and types of parameters expected by the lambda expression and its return type (if any).

Example of using lambda expression with `Func` delegate:

```csharp
Func<int, int, int> add = (x, y) => x + y;
```

3. **Multiple Parameters**:
   - Lambda expressions can accept multiple parameters separated by commas in the parameter list.

Example of a lambda expression with multiple parameters:

```csharp
Action<string, int> printDetails = (name, age) => Console.WriteLine($"Name: {name}, Age: {age}");
```

4. **Statement Body**:
   - If the body of the lambda expression contains more than one statement, you need to enclose it in curly braces `{ }`.

Example of a lambda expression with a statement body:

```csharp
Func<int, int> factorial = n =>
{
    int result = 1;
    for (int i = 1; i <= n; i++)
    {
        result *= i;
    }
    return result;
};
```

5. **Use Cases**:
   - Lambda expressions are commonly used with LINQ queries to define predicates, selectors, and projections.
   - They are also used as event handlers, asynchronous callbacks, and functional programming techniques such as map, reduce, and filter.

Lambda expressions provide a concise and expressive way to define inline delegate functions in C# .NET Core, making code more readable and maintainable, especially in scenarios involving functional programming and LINQ queries.