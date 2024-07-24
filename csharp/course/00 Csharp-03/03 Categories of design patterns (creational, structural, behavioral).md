Design patterns are commonly categorized into three main categories based on their purpose and usage: creational patterns, structural patterns, and behavioral patterns. Here's an overview of each category along with examples of design patterns in .NET Core using C#:

1. **Creational Patterns**:
   Creational patterns deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. They aim to provide flexibility in object creation while hiding the creation logic, thus making the system more independent of the specifics of object creation, composition, and representation.
   - **Singleton**: Ensures that a class has only one instance and provides a global point of access to that instance.
   - **Factory Method**: Defines an interface for creating objects but allows subclasses to alter the type of objects that will be created.
   - **Abstract Factory**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.

2. **Structural Patterns**:
   Structural patterns deal with object composition or, in other words, the way objects are composed to form larger structures. They focus on simplifying the structure of a system by identifying simple ways to realize relationships between entities.
   - **Adapter**: Allows objects with incompatible interfaces to collaborate.
   - **Decorator**: Adds behavior to objects dynamically without affecting the behavior of other objects from the same class.
   - **Facade**: Provides a unified interface to a set of interfaces in a subsystem.

3. **Behavioral Patterns**:
   Behavioral patterns focus on communication between objects, how they interact, and how they distribute responsibilities. They emphasize the interaction between objects, how they communicate, and how they are assigned various responsibilities within the system.
   - **Observer**: Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
   - **Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.
   - **Chain of Responsibility**: Avoids coupling the sender of a request to its receiver by giving more than one object a chance to handle the request.

In .NET Core with C#, you can implement these design patterns to improve the architecture, scalability, and maintainability of your applications. Each pattern addresses specific design concerns and provides solutions that have been refined and proven over time in various software development scenarios.