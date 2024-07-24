Iterators in .NET Core C# provide a convenient way to iterate over collections or generate sequences of data without the need to explicitly implement the entire IEnumerator interface. Instead, you can use the `yield` keyword to define an iterator method, making it easier to create custom iterators. Here's how iterators work in .NET Core C#:

### 1. Iterator Methods:

Iterator methods use the `yield` keyword to return each element of a sequence one at a time, allowing you to iterate over the sequence using a `foreach` loop or LINQ query. The `yield` keyword temporarily suspends the method's execution and returns control to the caller, preserving the method's state until the next iteration.

```csharp
public IEnumerable<int> GenerateNumbers(int count)
{
    for (int i = 1; i <= count; i++)
    {
        yield return i;
    }
}
```

### 2. Using Iterators:

You can use iterator methods in `foreach` loops or LINQ queries just like any other enumerable collection. The `foreach` loop automatically iterates over the sequence returned by the iterator method, and LINQ methods like `Select`, `Where`, and `OrderBy` can be applied to the sequence.

```csharp
foreach (int number in GenerateNumbers(5))
{
    Console.WriteLine(number);
}
```

### 3. Iterating over Collections:

You can use iterators to iterate over existing collections and apply custom logic or transformations to each element. This allows you to create lazy-evaluated sequences without the need to materialize the entire collection in memory.

```csharp
public IEnumerable<int> DoubleNumbers(IEnumerable<int> numbers)
{
    foreach (int number in numbers)
    {
        yield return number * 2;
    }
}
```

### 4. Benefits of Iterators:

- **Lazy Evaluation**: Iterators enable lazy evaluation, meaning that elements are generated on-demand as they are iterated over, conserving memory and improving performance.
  
- **Simplified Code**: Iterator methods simplify code by encapsulating the logic for generating sequences, making it easier to create custom iterators without the need for explicit state management.

- **Deferred Execution**: Iterators support deferred execution, allowing you to compose and chain multiple iterator methods together to create complex sequences efficiently.

### Summary:

Iterators in .NET Core C# provide a convenient way to generate sequences of data and iterate over collections lazily. By using the `yield` keyword in iterator methods, you can create custom iterators with minimal boilerplate code, improving code readability and maintainability. Let me know if you need further assistance or examples!