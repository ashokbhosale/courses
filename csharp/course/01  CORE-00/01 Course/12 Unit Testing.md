Unit testing is an essential part of software development, ensuring that individual components of your code work as expected. Both xUnit and MSTest are popular testing frameworks for .NET Core applications. Let's see examples of how to write unit tests using both frameworks.

### Using xUnit:

1. Install xUnit NuGet package:

```bash
dotnet add package xunit
dotnet add package xunit.runner.visualstudio
dotnet add package coverlet.collector
```

2. Write a unit test class:

```csharp
using Xunit;
using MyApplication;

namespace MyApplication.Tests
{
    public class CalculatorTests
    {
        [Fact]
        public void Add_ReturnsCorrectSum()
        {
            // Arrange
            var calculator = new Calculator();

            // Act
            var result = calculator.Add(3, 4);

            // Assert
            Assert.Equal(7, result);
        }

        [Fact]
        public void Subtract_ReturnsCorrectDifference()
        {
            // Arrange
            var calculator = new Calculator();

            // Act
            var result = calculator.Subtract(7, 3);

            // Assert
            Assert.Equal(4, result);
        }
    }
}
```

3. Run tests:

```bash
dotnet test
```

### Using MSTest:

1. Install MSTest NuGet package:

```bash
dotnet add package MSTest.TestFramework
dotnet add package MSTest.TestAdapter
```

2. Write a unit test class:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using MyApplication;

namespace MyApplication.Tests
{
    [TestClass]
    public class CalculatorTests
    {
        [TestMethod]
        public void Add_ReturnsCorrectSum()
        {
            // Arrange
            var calculator = new Calculator();

            // Act
            var result = calculator.Add(3, 4);

            // Assert
            Assert.AreEqual(7, result);
        }

        [TestMethod]
        public void Subtract_ReturnsCorrectDifference()
        {
            // Arrange
            var calculator = new Calculator();

            // Act
            var result = calculator.Subtract(7, 3);

            // Assert
            Assert.AreEqual(4, result);
        }
    }
}
```

3. Run tests:

```bash
dotnet test
```

Both xUnit and MSTest provide similar functionalities for writing and executing unit tests in .NET Core applications. Choose the one that suits your preferences and project requirements.