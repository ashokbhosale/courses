Sure, let's dive into each of the SOLID principles with examples in .NET Core C#:

1. **Single Responsibility Principle (SRP):**
   - This principle states that a class should have only one reason to change, i.e., it should have only one responsibility.
   - Example: In a .NET Core web application, you might have a class responsible for handling user authentication (`Authenticator`). Instead of adding other unrelated functionalities, such as user profile management, into this class, it's better to create a separate class for user profile management (`UserProfileManager`). This ensures that each class has a single responsibility.

2. **Open/Closed Principle (OCP):**
   - This principle states that software entities should be open for extension but closed for modification. It encourages the use of abstraction to achieve this goal.
   - Example: Consider a .NET Core application that calculates the area of different shapes (`Circle`, `Square`, etc.). Instead of modifying the existing code every time a new shape is added, you can create an interface `IShape` with a method `CalculateArea()` and have each shape implement this interface. Then, you can create a separate class (`AreaCalculator`) responsible for calculating the area of any shape by accepting objects of types implementing `IShape`. This way, new shapes can be added without modifying the existing `AreaCalculator` class.

3. **Liskov Substitution Principle (LSP):**
   - This principle states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program.
   - Example: In a .NET Core application, if you have a base class `Animal` with a method `MakeSound()`, and you have subclasses `Dog` and `Cat` inheriting from `Animal`, then you should be able to replace instances of `Animal` with instances of `Dog` or `Cat` without changing the behavior of the program.

4. **Interface Segregation Principle (ISP):**
   - This principle states that clients should not be forced to depend on interfaces they do not use. It's better to have multiple specific interfaces than a single large interface.
   - Example: Suppose you have a .NET Core interface `IWorker` with methods `Work()` and `TakeBreak()`. However, in your application, not all classes implementing `IWorker` need to take breaks. In such cases, it's better to split `IWorker` into smaller interfaces, like `IWorker` for work-related methods and `IBreakTaker` for break-related methods, to adhere to ISP.

5. **Dependency Inversion Principle (DIP):**
   - This principle states that high-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details; details should depend on abstractions.
   - Example: In a .NET Core application, instead of directly instantiating concrete implementations of dependencies in a high-level module, you can use dependency injection to provide dependencies through interfaces. This allows you to easily switch implementations without modifying the high-level module.

In .NET Core C# development, adhering to these SOLID principles results in code that is easier to maintain, extend, and test, ultimately leading to more robust and scalable applications.