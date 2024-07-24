**Object-Oriented Programming (OOP) with .NET Core:**

Object-Oriented Programming (OOP) is a programming paradigm that revolves around the concept of objects, which encapsulate data and behavior. In .NET Core, you can leverage OOP principles to write modular, maintainable, and scalable code. Let's explore some key OOP principles and how they are implemented in C# with .NET Core.

**1. Classes and Objects:**

- **Classes:** Classes are blueprints for creating objects. They define the properties (attributes) and methods (behavior) of objects.
- **Objects:** Objects are instances of classes. They represent real-world entities and encapsulate data and behavior.

```csharp
// Class definition
class Person
{
    // Properties
    public string Name { get; set; }
    public int Age { get; set; }

    // Method
    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I'm {Age} years old.");
    }
}

// Creating an object of the Person class
Person person1 = new Person();
person1.Name = "John";
person1.Age = 30;

// Calling a method on the object
person1.SayHello();
```

**2. Inheritance:**

Inheritance allows a class (subclass) to inherit properties and methods from another class (base class). It promotes code reuse and establishes a hierarchical relationship between classes.

```csharp
// Base class
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating...");
    }
}

// Derived class inheriting from the Animal class
class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Woof!");
    }
}

// Creating an object of the Dog class
Dog dog1 = new Dog();
dog1.Eat(); // Inherited method
dog1.Bark(); // Method specific to Dog class
```

**3. Encapsulation:**

Encapsulation is the bundling of data and methods that operate on the data within a single unit (class). It hides the internal state of an object and only exposes necessary functionality through methods.

```csharp
class BankAccount
{
    private decimal balance; // Encapsulated field

    public void Deposit(decimal amount)
    {
        balance += amount;
    }

    public void Withdraw(decimal amount)
    {
        balance -= amount;
    }

    public decimal GetBalance()
    {
        return balance;
    }
}
```

**4. Polymorphism:**

Polymorphism allows objects of different classes to be treated as objects of a common base class. It enables code to work with objects of multiple types through inheritance and method overriding.

```csharp
// Base class
class Shape
{
    public virtual void Draw()
    {
        Console.WriteLine("Drawing a shape...");
    }
}

// Derived class overriding the Draw method
class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle...");
    }
}

// Using polymorphism
Shape shape1 = new Circle();
shape1.Draw(); // Calls the Draw method of the Circle class
```

By understanding and applying these OOP principles, you can write more structured, modular, and maintainable code in .NET Core applications.