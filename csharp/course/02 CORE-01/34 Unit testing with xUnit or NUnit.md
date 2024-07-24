Unit testing with xUnit or NUnit in .NET Core C# involves writing tests to verify the behavior of individual units of code in your application. Let's see how to do it with both xUnit and NUnit along with examples:

### xUnit

1. **Install xUnit NuGet Package**:
   - Install the xUnit NuGet package for your test project.
   ```bash
   dotnet add package xunit
   dotnet add package xunit.runner.visualstudio
   ```

2. **Write Test Cases**:
   - Create test classes and write test methods using the xUnit framework attributes.
   ```csharp
   using Xunit;
   
   public class CalculatorTests
   {
       [Fact]
       public void Add_WhenAddingTwoNumbers_ReturnsSum()
       {
           // Arrange
           var calculator = new Calculator();

           // Act
           var result = calculator.Add(2, 3);

           // Assert
           Assert.Equal(5, result);
       }
   }
   ```

3. **Run Tests**:
   - Use the test runner in Visual Studio or run tests from the command line using `dotnet test`.

### NUnit

1. **Install NUnit NuGet Package**:
   - Install the NUnit NuGet package for your test project.
   ```bash
   dotnet add package NUnit
   dotnet add package NUnit3TestAdapter
   ```

2. **Write Test Cases**:
   - Create test classes and write test methods using the NUnit framework attributes.
   ```csharp
   using NUnit.Framework;
   
   [TestFixture]
   public class CalculatorTests
   {
       [Test]
       public void Add_WhenAddingTwoNumbers_ReturnsSum()
       {
           // Arrange
           var calculator = new Calculator();

           // Act
           var result = calculator.Add(2, 3);

           // Assert
           Assert.AreEqual(5, result);
       }
   }
   ```

3. **Run Tests**:
   - Use the test runner in Visual Studio or run tests from the command line using `dotnet test`.

### Example Calculator Class

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```

By following these steps and examples, you can perform unit testing with xUnit or NUnit in .NET Core C#. Writing and running tests helps ensure that your code behaves as expected, facilitating easier maintenance and refactoring while providing confidence in the quality of your software.