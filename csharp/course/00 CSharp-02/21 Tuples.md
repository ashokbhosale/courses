Tuples in C# provide a lightweight way to group multiple related values together. They are particularly useful when you need to return multiple values from a method without explicitly creating a custom type.

Here's how you can work with tuples in .NET Core C#:

1. **Creating Tuples**:
   You can create tuples using the `Tuple` class or, more conveniently, using tuple literals:

```csharp
var person = ("John", 30);
```

Here, `person` is a tuple with two elements, where the first element is a string ("John") and the second element is an integer (30).

2. **Accessing Tuple Elements**:
   You can access tuple elements using the `Item` property or through deconstruction:

```csharp
Console.WriteLine($"Name: {person.Item1}, Age: {person.Item2}");
// Output: Name: John, Age: 30

var (name, age) = person;
Console.WriteLine($"Name: {name}, Age: {age}");
// Output: Name: John, Age: 30
```

3. **Named Tuples**:
   You can create named tuples using tuple literals with named elements:

```csharp
var person = (Name: "John", Age: 30);
Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
// Output: Name: John, Age: 30
```

4. **Returning Tuples from Methods**:
   Tuples are commonly used to return multiple values from a method:

```csharp
public (string, int) GetPerson()
{
    return ("John", 30);
}

var person = GetPerson();
Console.WriteLine($"Name: {person.Item1}, Age: {person.Item2}");
// Output: Name: John, Age: 30
```

You can also use named tuples to make the returned values more descriptive:

```csharp
public (string Name, int Age) GetPerson()
{
    return ("John", 30);
}

var person = GetPerson();
Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
// Output: Name: John, Age: 30
```

5. **Tuple Deconstruction**:
   You can deconstruct tuples directly in method parameters or in `foreach` loops:

```csharp
(string name, int age) = GetPerson();
Console.WriteLine($"Name: {name}, Age: {age}");
// Output: Name: John, Age: 30

foreach (var (name, age) in new[] { ("John", 30), ("Alice", 25), ("Bob", 35) })
{
    Console.WriteLine($"Name: {name}, Age: {age}");
}
```

Tuples are handy for scenarios where you need a lightweight data structure to temporarily group related values, especially when the structure is simple and the data doesn't warrant defining a custom class.