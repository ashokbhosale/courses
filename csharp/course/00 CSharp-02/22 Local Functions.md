Local functions in C# allow you to define functions within the scope of another function. They are especially useful for encapsulating helper functions that are only needed within a particular method.

Here's how you can use local functions in .NET Core C#:

```csharp
public class MyClass
{
    public void MyMethod()
    {
        // Local function definition
        int Add(int a, int b)
        {
            return a + b;
        }

        int result = Add(3, 4);
        Console.WriteLine(result); // Output: 7
    }
}
```

In the above example:

- `Add` is a local function defined within the scope of the `MyMethod` method.
- Local functions have access to variables from the enclosing method's scope.
- They can access instance members of the containing class as well.

Local functions have some important characteristics:

1. **Accessibility**: Local functions have the same accessibility as the enclosing method. They can be private, protected, internal, or public.

2. **Capture Variables**: Local functions can capture variables from the enclosing scope, just like lambda expressions.

3. **No Separation of Concerns**: Local functions can help keep the logic of a method encapsulated and self-contained. They're particularly useful when the logic within a method gets complex and you need to break it down into smaller, more manageable parts.

4. **Performance**: Local functions can improve performance in some scenarios by avoiding the overhead of method calls. Since they're defined within the same method, the compiler can optimize their invocation.

5. **Debugging**: Local functions can be debugged just like regular methods. They have access to the same debugging features, making it easier to step through code during debugging sessions.

However, it's essential to use local functions judiciously. Overusing them can clutter the method's body and make the code harder to read. Reserve them for cases where they genuinely improve clarity and maintainability.