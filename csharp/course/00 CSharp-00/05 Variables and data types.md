In C#, variables are used to store data, and data types specify the type of data that can be stored in a variable. Here's an overview of variables and data types in C# .NET Core:

### Variables:

A variable is a named memory location used to store data. In C#, variables must be declared before they can be used. The syntax for declaring a variable is:

```csharp
<datatype> <variableName>;
```

For example:
```csharp
int age;
string name;
```

### Data Types:

C# supports various built-in data types, each designed to store different kinds of data. Here are some common data types in C#:

1. **Numeric Types**:
   - `int`: Represents signed 32-bit integers (-2,147,483,648 to 2,147,483,647).
   - `double`: Represents double-precision floating-point numbers (±5.0 × 10^-324 to ±1.7 × 10^308).
   - `float`: Represents single-precision floating-point numbers (±1.5 × 10^-45 to ±3.4 × 10^38).
   - `decimal`: Represents decimal numbers with higher precision (±1.0 x 10^-28 to ±7.9 x 10^28).

2. **Boolean Type**:
   - `bool`: Represents boolean values (true or false).

3. **Character Types**:
   - `char`: Represents a single Unicode character.

4. **String Type**:
   - `string`: Represents a sequence of characters.

5. **Other Types**:
   - `byte`: Represents unsigned 8-bit integers (0 to 255).
   - `short`: Represents signed 16-bit integers (-32,768 to 32,767).
   - `long`: Represents signed 64-bit integers (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807).
   - `uint`, `ushort`, `ulong`: Represents unsigned versions of `int`, `short`, and `long` respectively.
   - `object`: Represents an instance of any type.

### Example:

```csharp
// Numeric types
int age = 30;
double price = 10.99;
bool isStudent = true;
char grade = 'A';
string message = "Hello, world!";

// Output variables
Console.WriteLine($"Age: {age}");
Console.WriteLine($"Price: {price}");
Console.WriteLine($"Is student: {isStudent}");
Console.WriteLine($"Grade: {grade}");
Console.WriteLine($"Message: {message}");
```

### Variable Initialization:

Variables can be initialized at the time of declaration:

```csharp
int age = 30;
string name = "John";
```

### Implicit Type Declaration (var):

In C#, you can use the `var` keyword to declare variables implicitly. The compiler infers the type based on the value assigned:

```csharp
var age = 30;
var name = "John";
```

### Note:

- Variable names must follow C# identifier naming rules.
- C# is a statically-typed language, meaning once a variable is declared with a specific type, its type cannot be changed.
- C# supports both value types (stored in the stack) and reference types (stored in the heap).