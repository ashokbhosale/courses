Certainly! Let's delve into SOLID principles and some common design patterns with examples in .NET Core C#:

### SOLID Principles:

1. **Single Responsibility Principle (SRP)**:
   - A class should have only one reason to change.
   - Example: Separating data access logic and business logic into separate classes.

2. **Open/Closed Principle (OCP)**:
   - Software entities should be open for extension but closed for modification.
   - Example: Using interfaces and abstract classes for extensions.

3. **Liskov Substitution Principle (LSP)**:
   - Objects of a superclass should be replaceable with objects of its subclasses.
   - Example: Ensuring derived classes can substitute base classes without altering program correctness.

4. **Interface Segregation Principle (ISP)**:
   - Clients should not be forced to depend on interfaces they do not use.
   - Example: Breaking down large interfaces into smaller, more specific ones.

5. **Dependency Inversion Principle (DIP)**:
   - High-level modules should not depend on low-level modules. Both should depend on abstractions.
   - Example: Using dependency injection to invert the dependency relationship between classes.

### Common Design Patterns:

1. **Singleton Pattern**:
   - Ensures a class has only one instance and provides a global access point to it.
   - Example:

     ```csharp
     public class Singleton
     {
         private static readonly Singleton instance = new Singleton();

         private Singleton() { }

         public static Singleton Instance
         {
             get { return instance; }
         }
     }
     ```

2. **Factory Pattern**:
   - Defines an interface for creating objects but allows subclasses to alter the type of objects that will be created.
   - Example:

     ```csharp
     public interface IFactory
     {
         Product CreateProduct();
     }

     public class ConcreteFactory : IFactory
     {
         public Product CreateProduct()
         {
             return new ConcreteProduct();
         }
     }
     ```

3. **Observer Pattern**:
   - Defines a one-to-many dependency between objects where a change in one object triggers updates in its dependents.
   - Example:

     ```csharp
     public interface IObserver
     {
         void Update();
     }

     public class ConcreteObserver : IObserver
     {
         public void Update()
         {
             // Update logic
         }
     }

     public class Subject
     {
         private readonly List<IObserver> observers = new List<IObserver>();

         public void Attach(IObserver observer)
         {
             observers.Add(observer);
         }

         public void Notify()
         {
             foreach (var observer in observers)
             {
                 observer.Update();
             }
         }
     }
     ```

These principles and patterns provide guidelines and templates for designing robust, flexible, and maintainable software in .NET Core C#. Integrating them into your development practices can greatly enhance the quality and scalability of your applications.