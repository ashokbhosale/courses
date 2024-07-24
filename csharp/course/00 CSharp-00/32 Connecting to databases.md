Connecting to databases with .NET Core C# involves selecting an appropriate database provider, establishing a connection, and executing queries or commands to interact with the database. Here's a step-by-step guide on how to connect to databases in .NET Core C#:

1. **Choose a Database Provider**:
   - Decide on the database engine you want to use (e.g., SQL Server, MySQL, PostgreSQL, SQLite).
   - Select the corresponding database provider package for .NET Core from NuGet.

2. **Install Database Provider Package**:
   - Use NuGet Package Manager or .NET CLI to install the database provider package. For example:
     ```
     dotnet add package Microsoft.EntityFrameworkCore.SqlServer
     ```

3. **Configure Database Connection**:
   - Define the connection string for your database in the application configuration file (`appsettings.json` or `appsettings.Development.json`).
   - Specify the server address, database name, authentication credentials, and other necessary parameters.

4. **Create Database Context**:
   - Create a database context class that inherits from `DbContext` provided by Entity Framework Core.
   - Define properties representing database tables as `DbSet<T>` properties.
   - Override `OnConfiguring` method to configure the database connection using the connection string.

5. **Perform Database Operations**:
   - Use LINQ queries or SQL commands to perform CRUD (Create, Read, Update, Delete) operations on the database.
   - Use methods like `Add`, `FirstOrDefault`, `ToList`, `SaveChanges`, etc., to manipulate data.

6. **Handle Database Errors**:
   - Implement error handling mechanisms to deal with database-related exceptions, such as connection failures, constraint violations, or timeouts.
   - Utilize try-catch blocks or global exception handlers to catch and handle exceptions gracefully.

Example of connecting to a SQL Server database using Entity Framework Core:

```csharp
using Microsoft.EntityFrameworkCore;

public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        string connectionString = "Server=myServerAddress;Database=myDatabase;User Id=myUsername;Password=myPassword;";
        optionsBuilder.UseSqlServer(connectionString);
    }
}

public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}

class Program
{
    static void Main()
    {
        using (var context = new MyDbContext())
        {
            // Perform database operations
            var products = context.Products.ToList();
        }
    }
}
```

This example demonstrates connecting to a SQL Server database using Entity Framework Core. Replace `"Server=myServerAddress;Database=myDatabase;User Id=myUsername;Password=myPassword;"` with your actual connection string. Then, you can use the `MyDbContext` class to interact with the database and perform CRUD operations on the `Products` table.