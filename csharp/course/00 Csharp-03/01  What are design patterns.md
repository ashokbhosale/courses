Design patterns are general reusable solutions to commonly occurring problems in software design. They represent best practices evolved over time by experienced software developers. Design patterns are language-agnostic concepts, so they can be applied in any programming language, including C# with .NET Core.

In C# with .NET Core, you can apply various design patterns to improve the structure, readability, and maintainability of your code. Some commonly used design patterns in C# include:

1. **Creational Patterns**:
   - **Singleton**: Ensures that a class has only one instance and provides a global point of access to that instance.
   - **Factory Method**: Defines an interface for creating an object but allows subclasses to alter the type of objects that will be created.
   - **Abstract Factory**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.

2. **Structural Patterns**:
   - **Adapter**: Allows objects with incompatible interfaces to collaborate.
   - **Decorator**: Adds behavior to objects dynamically without affecting the behavior of other objects from the same class.
   - **Facade**: Provides a unified interface to a set of interfaces in a subsystem.

3. **Behavioral Patterns**:
   - **Observer**: Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
   - **Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
   - **Chain of Responsibility**: Avoids coupling the sender of a request to its receiver by giving more than one object a chance to handle the request.

These are just a few examples, and there are many more design patterns that you can utilize in your C# projects. Implementing design patterns can make your code more modular, easier to understand, and easier to maintain. In .NET Core, you can leverage these patterns to build robust and scalable applications.