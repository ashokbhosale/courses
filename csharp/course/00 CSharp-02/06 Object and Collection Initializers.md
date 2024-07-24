Object and collection initializers in .NET Core C# provide a concise syntax for initializing objects and collections directly within their declarations. This allows you to initialize properties or add elements to collections in a single expression, improving code readability and reducing the need for additional constructor overloads. Here's how you can use object and collection initializers:

### 1. Object Initializers:

Object initializers allow you to initialize the properties of an object directly within its declaration. You can specify property names and values using the `{}` syntax.

```csharp
public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

// Object initializer
Person person = new Person { FirstName = "John", LastName = "Doe" };
```

### 2. Collection Initializers:

Collection initializers allow you to add elements to collections directly within their declaration. You can use the `{}` syntax to specify the elements to add to the collection.

```csharp
// Collection initializer
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
```

### 3. Nested Object and Collection Initializers:

You can use nested object and collection initializers to initialize nested objects or collections.

```csharp
public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}

public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public Address HomeAddress { get; set; }
}

// Nested object initializer
Person person = new Person
{
    FirstName = "John",
    LastName = "Doe",
    HomeAddress = new Address { Street = "123 Main St", City = "Anytown" }
};
```

### 4. Collection Initializers with Add Method:

For types that implement the `Add` method, you can use collection initializers with the `Add` method instead of the `{}` syntax.

```csharp
public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public List<string> Hobbies { get; } = new List<string>();

    public void AddHobby(string hobby)
    {
        Hobbies.Add(hobby);
    }
}

// Collection initializer with Add method
Person person = new Person
{
    FirstName = "John",
    LastName = "Doe",
    Hobbies = { "Reading", "Cooking", "Gardening" }
};
```

### Summary:

Object and collection initializers in .NET Core C# provide a concise and convenient way to initialize objects and collections directly within their declarations. By understanding how to use object and collection initializers, you can improve code readability and reduce the need for additional constructor overloads in your .NET Core projects. Let me know if you need further assistance or examples!