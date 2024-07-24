In .NET Core (now .NET 5 and beyond), you can override and implement methods using inheritance and interfaces respectively, just like in other object-oriented programming languages. Here's how you can do it:

### Overriding Methods (Inheritance)
When you inherit from a base class, you can override its methods in the derived class. Here's an example:

```csharp
public class BaseClass
{
    public virtual void MethodToOverride()
    {
        Console.WriteLine("Base class method.");
    }
}

public class DerivedClass : BaseClass
{
    public override void MethodToOverride()
    {
        Console.WriteLine("Derived class method.");
    }
}
```

In the above example, `DerivedClass` overrides the `MethodToOverride` method from `BaseClass`.

### Implementing Methods (Interfaces)
When you implement an interface, you are essentially agreeing to provide definitions for all of its members (methods, properties, events). Here's an example:

```csharp
public interface IExampleInterface
{
    void ExampleMethod();
}

public class ImplementingClass : IExampleInterface
{
    public void ExampleMethod()
    {
        Console.WriteLine("Implementing method.");
    }
}
```

In this case, `ImplementingClass` implements the `IExampleInterface` and thus provides the implementation for the `ExampleMethod`.

### Example Using Both Inheritance and Interface Implementation

```csharp
using System;

public interface IExampleInterface
{
    void ExampleMethod();
}

public class BaseClass
{
    public virtual void MethodToOverride()
    {
        Console.WriteLine("Base class method.");
    }
}

public class DerivedClass : BaseClass, IExampleInterface
{
    public override void MethodToOverride()
    {
        Console.WriteLine("Derived class method.");
    }

    public void ExampleMethod()
    {
        Console.WriteLine("Implementing method.");
    }
}

class Program
{
    static void Main()
    {
        DerivedClass obj = new DerivedClass();
        obj.MethodToOverride(); // Output: Derived class method.
        obj.ExampleMethod();    // Output: Implementing method.
    }
}
```

In this example, `DerivedClass` both overrides a method from `BaseClass` and implements a method from `IExampleInterface`. 

That's the basics of overriding and implementing methods in .NET Core using C#. Let me know if you need further explanation or examples!