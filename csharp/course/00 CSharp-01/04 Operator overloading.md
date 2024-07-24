Operator overloading allows you to define custom behavior for operators such as +, -, *, /, etc., for your custom types. In C#, you can overload operators using the `operator` keyword. Here's how you can do it in .NET Core C#:

```csharp
using System;

public class Vector2D
{
    public double X { get; set; }
    public double Y { get; set; }

    public Vector2D(double x, double y)
    {
        X = x;
        Y = y;
    }

    // Overloading the + operator for Vector2D
    public static Vector2D operator +(Vector2D v1, Vector2D v2)
    {
        return new Vector2D(v1.X + v2.X, v1.Y + v2.Y);
    }

    // Overloading the - operator for Vector2D
    public static Vector2D operator -(Vector2D v1, Vector2D v2)
    {
        return new Vector2D(v1.X - v2.X, v1.Y - v2.Y);
    }

    // Overloading the * operator for Vector2D and scalar multiplication
    public static Vector2D operator *(Vector2D v, double scalar)
    {
        return new Vector2D(v.X * scalar, v.Y * scalar);
    }

    // Overriding the ToString method to provide a string representation of the vector
    public override string ToString()
    {
        return $"({X}, {Y})";
    }
}

class Program
{
    static void Main()
    {
        Vector2D v1 = new Vector2D(1, 2);
        Vector2D v2 = new Vector2D(3, 4);

        Vector2D sum = v1 + v2;
        Vector2D difference = v1 - v2;
        Vector2D scaled = v1 * 2;

        Console.WriteLine($"Sum: {sum}"); // Output: Sum: (4, 6)
        Console.WriteLine($"Difference: {difference}"); // Output: Difference: (-2, -2)
        Console.WriteLine($"Scaled: {scaled}"); // Output: Scaled: (2, 4)
    }
}
```

In this example:

- We define a `Vector2D` class representing a 2D vector.
- We overload the `+`, `-`, and `*` operators for vector addition, subtraction, and scalar multiplication respectively.
- We override the `ToString` method to provide a string representation of the vector for easy printing.

That's how you can overload operators in .NET Core C#. Let me know if you need further clarification or more examples!