**C# Language Fundamentals:**

C# is a powerful and versatile programming language used for building a wide range of applications, from simple console applications to complex web and desktop applications. Mastering the basics of C# is essential for becoming proficient in software development.

**1. Variables and Data Types:**

Variables are used to store data in memory during program execution. In C#, variables must be declared before they can be used, and each variable has a specific data type that determines the kind of data it can hold.

```csharp
// Variable declaration and initialization
int age = 30;
string name = "John";
double height = 6.2;
bool isMarried = false;
```

**2. Control Flow:**

Control flow statements allow you to control the execution flow of your program based on certain conditions.

- **if-else Statements:**
```csharp
int x = 10;
if (x > 5)
{
    Console.WriteLine("x is greater than 5");
}
else
{
    Console.WriteLine("x is less than or equal to 5");
}
```

- **switch Statement:**
```csharp
int dayOfWeek = 3;
switch (dayOfWeek)
{
    case 1:
        Console.WriteLine("Monday");
        break;
    case 2:
        Console.WriteLine("Tuesday");
        break;
    // More cases...
    default:
        Console.WriteLine("Invalid day");
        break;
}
```

- **Loops (for, while, do-while):**
```csharp
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(i);
}

int j = 0;
while (j < 5)
{
    Console.WriteLine(j);
    j++;
}

int k = 0;
do
{
    Console.WriteLine(k);
    k++;
} while (k < 5);
```

**3. Functions:**

Functions (or methods) are reusable blocks of code that perform a specific task. They help in organizing code and making it more modular and maintainable.

```csharp
// Function definition
void PrintHello()
{
    Console.WriteLine("Hello, World!");
}

// Function call
PrintHello();
```

Functions can also accept parameters and return values:

```csharp
// Function with parameters and return value
int Add(int a, int b)
{
    return a + b;
}

// Function call with arguments
int result = Add(5, 3);
Console.WriteLine("Result: " + result); // Output: 8
```

By mastering these basics of C#, you'll be well-equipped to tackle more complex programming tasks and build robust applications in .NET Core.