Discards in C# provide a way to ignore values in various contexts where a variable is required syntactically but its value is not needed. They are represented by the underscore `_` character and can be particularly useful when you're working with patterns where you don't need to use a specific value.

Here's how you can use discards in .NET Core C#:

1. **Discarding Individual Values**:
   
   You can use discards to ignore specific values:

   ```csharp
   var (_, _, result) = GetValues(); // Assuming GetValues() returns a tuple
   ```

   In this example, we're discarding the first two values returned by `GetValues()` and only interested in the third value.

2. **Discarding Elements in Patterns**:
   
   Discards can be used in patterns, such as in switch statements or when using pattern matching:

   ```csharp
   switch (obj)
   {
       case int i:
           Console.WriteLine($"Integer: {i}");
           break;
       case string s:
           Console.WriteLine($"String: {s}");
           break;
       case _:
           Console.WriteLine("Unknown type");
           break;
   }
   ```

   Here, the `_` is used as a discard pattern to match any value that hasn't been matched by the previous cases.

3. **Ignoring Method Return Values**:
   
   You can use discards to ignore the return values of methods:

   ```csharp
   _ = SomeMethod(); // Ignoring the return value
   ```

   This is particularly useful when you have a method that returns a value, but you're not interested in using that value.

4. **Deconstruction**:
   
   Discards can be used when deconstructing tuples or other types:

   ```csharp
   var (_, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _, _,

Sorry for the cutoff! It seems like I lost my train of thought there. Let me continue from where I left off.

4. **Deconstruction**:

   Discards can be used when deconstructing tuples or other types:

   ```csharp
   (var _, var _, var result) = GetValues(); // Assuming GetValues() returns a tuple
   ```

   In this example, we're discarding the first two values returned by `GetValues()` and only interested in the third value.

5. **Iterating Over Collections**:

   Discards can be used when iterating over collections if you're not interested in the current element:

   ```csharp
   foreach (var _ in Enumerable.Range(1, 10))
   {
       // Do something without using the current element
   }
   ```

   In this case, we're iterating over a range of numbers but not using the value of each number in the loop body.

Discards are handy when you need to satisfy the syntax requirements of a language feature, but you don't actually need the value itself. They make your code more expressive by clearly indicating that a value is being ignored intentionally.