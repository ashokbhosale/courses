Automatic properties in .NET Core C# provide a concise syntax for defining properties without explicitly declaring backing fields. They simplify property declaration, reduce boilerplate code, and improve code readability. Here's how you can use automatic properties:

### 1. Syntax:

```csharp
public class Person
{
    public string FirstName { get; set; } // Automatic property with both getter and setter
    public string LastName { get; } // Automatic property with only getter
}
```

In the above example:
- `FirstName` is an automatic property with both getter and setter.
- `LastName` is an automatic property with only a getter. It can only be initialized in the constructor or inline.

### 2. Benefits:

- **Simplified Syntax**: Automatic properties eliminate the need to explicitly declare backing fields, reducing boilerplate code.
  
- **Encapsulation**: Automatic properties encapsulate the data, providing access through getter and setter methods.
  
- **Compiler-Generated Backing Field**: The compiler generates a hidden backing field for automatic properties, ensuring data storage.

### 3. Accessing Automatic Properties:

You can access automatic properties just like regular properties, using dot notation:

```csharp
Person person = new Person();
person.FirstName = "John"; // Set value
string firstName = person.FirstName; // Get value
```

### 4. Initializing Automatic Properties:

Automatic properties can be initialized directly when declaring them or in the class constructor:

```csharp
public class Person
{
    public string FirstName { get; set; } = "John"; // Initialize directly
    public string LastName { get; } // Automatic property with only getter

    public Person()
    {
        LastName = "Doe"; // Initialize in constructor
    }
}
```

### 5. Restrictions:

- Automatic properties cannot have different access modifiers for the getter and setter. Both must have the same access level.
  
- Additional logic in the getter or setter is not allowed. If you need additional logic, use traditional properties with explicit backing fields.

### Summary:

Automatic properties in .NET Core C# provide a concise and convenient way to define properties without explicitly declaring backing fields. By understanding the syntax and benefits of automatic properties, you can simplify property declaration and improve code readability in your .NET Core projects. Let me know if you need further assistance or examples!