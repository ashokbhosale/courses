Lambda expressions in .NET Core C# provide a concise way to write anonymous methods or functions inline. They are commonly used in LINQ queries, event handlers, and functional programming constructs. Here's how you can use lambda expressions in .NET Core:

### 1. Syntax:

Lambda expressions have the following syntax:

```csharp
(parameters) => expression_or_statement_block
```

For example, a lambda expression that takes two integers and returns their sum:

```csharp
(int a, int b) => a + b
```

### 2. Single-line Lambda Expressions:

For simple expressions, you can omit the curly braces `{}` and the `return` keyword:

```csharp
Func<int, int, int> add = (a, b) => a + b;
```

### 3. Multi-line Lambda Expressions:

For more complex logic, you can use curly braces `{}` and include multiple statements:

```csharp
Func<int, int, int> add = (a, b) =>
{
    int result = a + b;
    return result;
};
```

### 4. Using Lambda Expressions:

Lambda expressions are commonly used in LINQ queries to define filtering, projection, and sorting logic:

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0);
```

### 5. Lambda Expressions with Delegates:

Lambda expressions can be assigned to delegates, allowing you to create delegate instances inline:

```csharp
Action<int> printNumber = n => Console.WriteLine(n);
printNumber(10); // Output: 10
```

### 6. Lambda Expressions with LINQ:

Lambda expressions are extensively used in LINQ queries for defining predicates, projections, and ordering functions:

```csharp
var result = people
    .Where(person => person.Age > 18)
    .OrderBy(person => person.LastName)
    .Select(person => person.FirstName);
```

### Summary:

Lambda expressions in .NET Core C# provide a concise and expressive way to define anonymous methods or functions inline. By understanding the syntax and usage of lambda expressions, you can write more readable and compact code, especially in LINQ queries and event handlers. Let me know if you need further assistance or examples!