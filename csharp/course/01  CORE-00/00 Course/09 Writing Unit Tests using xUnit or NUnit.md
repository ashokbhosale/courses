**Writing Unit Tests using xUnit or NUnit:**

Both xUnit and NUnit are popular unit testing frameworks for .NET Core applications. They provide a way to write automated tests to verify the behavior of individual units of code, such as classes or methods.

```csharp
// Example of a unit test using xUnit
public class CalculatorTests
{
    [Fact]
    public void Add_ShouldReturnSum()
    {
        // Arrange
        var calculator = new Calculator();

        // Act
        var result = calculator.Add(3, 5);

        // Assert
        Assert.Equal(8, result);
    }
}
```

**Debugging Techniques and Tools in Visual Studio or Visual Studio Code:**

Visual Studio and Visual Studio Code are powerful IDEs with built-in debugging tools that allow you to inspect and debug your .NET Core applications. You can set breakpoints, step through code, watch variables, and analyze call stacks to identify and fix issues.

**Test-driven Development (TDD) Principles:**

Test-Driven Development (TDD) is a software development approach where tests are written before the actual code is implemented. The TDD cycle typically consists of three steps: writing a failing test, implementing the code to make the test pass, and refactoring the code to improve its design without changing its behavior.

```csharp
// Example of TDD approach
public class CalculatorTests
{
    [Fact]
    public void Add_ShouldReturnSum()
    {
        // Arrange
        var calculator = new Calculator();

        // Act
        var result = calculator.Add(3, 5);

        // Assert
        Assert.Equal(8, result);
    }
}

// Calculator class implementation
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```

By following the TDD approach, you ensure that your code is thoroughly tested and meets the specified requirements from the start of development.