**Object-Oriented Programming (OOP) with C#:**

Object-Oriented Programming (OOP) is a programming paradigm that revolves around the concept of objects, which can contain data in the form of fields and behaviors in the form of methods. In C#, OOP is fundamental, and it supports key OOP concepts such as classes, objects, inheritance, polymorphism, encapsulation, abstract classes, and interfaces.

**Understanding OOP Concepts:**

1. **Classes and Objects:** Classes are blueprints for creating objects. They define the properties (fields) and behaviors (methods) that objects of the class will have. Objects are instances of classes that hold specific values for their properties and can perform actions defined by the methods.

2. **Inheritance:** Inheritance allows a class (derived class) to inherit properties and behaviors from another class (base class). This promotes code reuse and allows for creating hierarchical relationships between classes.

3. **Polymorphism:** Polymorphism allows objects of different classes to be treated as objects of a common base class. This enables flexibility and extensibility in code by allowing methods to behave differently based on the object they operate on.

4. **Encapsulation:** Encapsulation is the practice of hiding the internal details of an object and only exposing a public interface through which the object can be interacted with. This helps in achieving data hiding, abstraction, and modularity.

**Creating and Using Classes and Objects in C#:**

```csharp
// Defining a class
public class Person
{
    // Fields
    public string Name { get; set; }
    public int Age { get; set; }

    // Constructor
    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Method
    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}

// Creating objects of the class
Person person1 = new Person("John", 30);
Person person2 = new Person("Alice", 25);

// Accessing properties and methods of objects
Console.WriteLine(person1.Name); // Output: John
person2.SayHello(); // Output: Hello, my name is Alice and I am 25 years old.
```

**Inheritance and Interface Implementation:**

```csharp
// Base class
public class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

// Derived class
public class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog barks");
    }
}

// Interface
public interface IWalkable
{
    void Walk();
}

// Class implementing interface
public class Cat : Animal, IWalkable
{
    public void Walk()
    {
        Console.WriteLine("Cat walks");
    }
}
```

**Abstract Classes and Interfaces:**

```csharp
// Abstract class
public abstract class Shape
{
    public abstract double Area();
}

// Concrete class inheriting from abstract class
public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double Area()
    {
        return Width * Height;
    }
}

// Interface
public interface IDrawable
{
    void Draw();
}

// Class implementing interface
public class Circle : IDrawable
{
    public void Draw()
    {
        Console.WriteLine("Drawing a circle");
    }
}
```

**Working with Access Modifiers:**

Access modifiers control the accessibility of types and members in C#. They include public, private, protected, internal, and protected internal.

```csharp
public class MyClass
{
    // Public field accessible from anywhere
    public int PublicField;

    // Private field accessible only within the class
    private int PrivateField;

    // Protected field accessible within the class and its derived classes
    protected int ProtectedField;

    // Internal field accessible within the same assembly
    internal int InternalField;

    // Protected internal field accessible within the same assembly or derived classes
    protected internal int ProtectedInternalField;
}
```

These examples demonstrate how to apply key OOP concepts in C# using .NET Core. Understanding and utilizing these concepts will help you design and implement robust, maintainable, and extensible software solutions.