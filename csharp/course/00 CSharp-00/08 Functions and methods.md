In C#, functions are referred to as methods. Methods are blocks of code that perform a specific task and can be called or invoked from other parts of your program. Here's an overview of functions and methods in C# .NET Core:

### Method Syntax:

```csharp
<access-modifier> <return-type> <method-name>(<parameters>)
{
    // Method body
}
```

- `<access-modifier>`: Specifies the visibility of the method (`public`, `private`, `protected`, `internal`, etc.).
- `<return-type>`: Specifies the type of value the method returns (`void` if the method doesn't return a value).
- `<method-name>`: The name of the method.
- `<parameters>`: Optional parameters that the method accepts.

### Example:

```csharp
public int Add(int x, int y)
{
    return x + y;
}
```

### Access Modifiers:

- **Public**: The method is accessible from any code in the same assembly or referencing assembly.
- **Private**: The method is accessible only from within the same class.
- **Protected**: The method is accessible within the same class or by derived classes.
	-Q.is protected method can be access from outside assembly also?
	No, a protected method cannot be accessed directly from outside the assembly, even if it's inherited by a derived class in another assembly. 
	
	The `protected` access modifier limits access to members (methods, properties, fields) to the containing class or types derived from it. However, this access is restricted to classes within the same assembly.
	
	Here's an example to illustrate this:
	
	```csharp
	// Assembly A
	using System;
	
	// Base class
	public class Shape
	{
	    // Protected method
	    protected void Display()
	    {
	        Console.WriteLine("This is a shape.");
	    }
	}
	
	// Assembly B (Different assembly)
	// Derived class
	public class Rectangle : Shape
	{
	    public void PrintInfo()
	    {
	        // Trying to access protected method from a derived class in a different assembly
	        // This will result in a compilation error
	        // Error CS1540: Cannot access protected member 'Shape.Display()' via a qualifier of type 'Rectangle'; 
	        // the qualifier must be of type 'Rectangle' (or derived from it)
	        // Display();
	    }
	}
	```
	
	In this example, if you try to call the `Display()` method from the `Rectangle` class, which is in a different assembly, you'll encounter a compilation error stating that the protected member cannot be accessed from outside the assembly.

Protected members are accessible only within the class that defines them and within derived classes, regardless of whether those derived classes are in the same or different assemblies.
- **Internal**: The method is accessible from within the same assembly.
- **Protected Internal**: The method is accessible within the same assembly or by derived classes.
	n C#, the `protected internal` access modifier allows a member (such as a method or property) to be accessed within the same assembly or by derived classes, whether they are in the same assembly or a different one. This access modifier provides a combination of both `protected` and `internal` access levels. Here's an example to demonstrate the usage of `protected internal`:

```csharp
using System;

// Base class
public class Shape
{
    // Protected internal method
    protected internal void Display()
    {
        Console.WriteLine("This is a shape.");
    }
}

// Derived class in the same assembly
public class Rectangle : Shape
{
    public void PrintInfo()
    {
        // Accessing protected internal method within the same assembly
        Display();
    }
}

// Derived class in a different assembly
// Assuming this file is in a different assembly
public class Circle : Shape
{
    public void PrintInfo()
    {
        // Accessing protected internal method from a derived class in a different assembly
        Display();
    }
}

// Main class
class Program
{
    static void Main(string[] args)
    {
        Rectangle rectangle = new Rectangle();
        rectangle.PrintInfo(); // This will print: "This is a shape."

        Circle circle = new Circle();
        circle.PrintInfo(); // This will also print: "This is a shape."
    }
}
```

In this example:

- We have a base class `Shape` with a `protected internal` method `Display()`.
- We then have two derived classes `Rectangle` and `Circle`.
- Both `Rectangle` and `Circle` can access the `Display()` method of the `Shape` class because they are either derived classes (`Rectangle`) or in the same assembly (`Circle`).
### Return Type:

The return type specifies the type of value that the method returns. It can be any valid C# data type, or `void` if the method doesn't return a value.

### Parameters:

Parameters are variables that are passed to the method when it's called. They allow you to provide input to the method. Parameters can be of any valid C# data type.

### Calling Methods:

To call a method, you use the method name followed by parentheses, optionally passing any required parameters.

```csharp
int result = Add(5, 3);
```

### Example with a Void Method:

```csharp
public void PrintMessage(string message)
{
    Console.WriteLine(message);
}
```

### Method Overloading:

Method overloading allows you to define multiple methods with the same name but different parameter lists. The compiler determines which method to call based on the number and types of arguments passed.

```csharp
public int Add(int x, int y)
{
    return x + y;
}

public double Add(double x, double y)
{
    return x + y;
}
```

### Summary:

Methods in C# provide a way to encapsulate code into reusable blocks, improving code organization and maintainability. They allow you to perform specific tasks, accept input parameters, and return results. By understanding method syntax and usage, you can create more modular and flexible C# .NET Core applications.