In C# and .NET Core, query expressions are syntactic sugar provided by LINQ (Language Integrated Query) to write queries against collections in a more readable and intuitive way. They allow you to query and manipulate data in a declarative manner, similar to SQL. Here's how you can use query expressions in .NET Core C#:

### 1. Basic Syntax:

The basic syntax of a query expression consists of a `from` clause followed by optional `where`, `orderby`, `groupby`, `select`, and `into` clauses.

```csharp
var query = from item in collection
            where condition
            orderby property ascending/descending
            select item;
```

### 2. Example:

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };

var query = from number in numbers
            where number % 2 == 0
            orderby number descending
            select number;
```

### 3. Query Operators:

- **from**: Specifies the data source and a range variable to represent each element in the source.
  
- **where**: Filters the elements based on a specified condition.
  
- **orderby**: Orders the elements based on a specified property or key.
  
- **select**: Projects each element of the source into a new form.

### 4. Additional Clauses:

- **groupby**: Groups the elements based on a specified key.
  
- **into**: Enables you to create a continuation query to further process the results of the initial query.

### 5. Fluent Syntax vs. Query Syntax:

In addition to query expressions, you can use method syntax (fluent syntax) to write LINQ queries. Both syntaxes are equivalent, and you can choose the one that fits your preference or the specific requirements of your code.

```csharp
// Fluent syntax equivalent of the previous query expression
var query = numbers.Where(number => number % 2 == 0)
                   .OrderByDescending(number => number)
                   .Select(number => number);
```

### 6. Deferred Execution:

LINQ queries use deferred execution, meaning that they are not executed until you iterate over the result or use methods like `ToList()`, `ToArray()`, or `FirstOrDefault()`.

### Summary:

Query expressions in .NET Core C# provide a powerful and intuitive way to query and manipulate data in collections. By understanding their syntax and usage, you can write concise and expressive code for data querying tasks in your .NET Core applications. Let me know if you need further assistance or examples!