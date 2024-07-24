Entity Framework Core (EF Core) is a powerful Object-Relational Mapping (ORM) framework that simplifies data access and manipulation in .NET Core applications. It provides a wide range of advanced features for working with databases. Here are some of the advanced features of Entity Framework Core in .NET Core C#:

### 1. Querying

#### LINQ Queries

- EF Core supports LINQ (Language-Integrated Query) for querying data from databases using familiar C# syntax.

```csharp
var query = dbContext.Products
    .Where(p => p.Category == "Electronics")
    .OrderBy(p => p.Price)
    .ToList();
```

#### Eager Loading

- Use `Include` method to eagerly load related entities to avoid lazy loading overhead.

```csharp
var product = dbContext.Products
    .Include(p => p.Category)
    .FirstOrDefault(p => p.Id == productId);
```

#### Explicit Loading

- Load related entities explicitly using `Load` method.

```csharp
var order = dbContext.Orders.FirstOrDefault();
dbContext.Entry(order).Collection(o => o.OrderItems).Load();
```

### 2. Performance Optimization

#### Batch Operations

- Use `AddRange`, `UpdateRange`, `RemoveRange` for batch operations to improve performance.

```csharp
dbContext.AddRange(orders);
dbContext.SaveChanges();
```

#### Raw SQL Queries

- Execute raw SQL queries for scenarios where LINQ is not suitable or for performance optimization.

```csharp
var products = dbContext.Products.FromSqlRaw("SELECT * FROM Products WHERE Price > {0}", minPrice).ToList();
```

### 3. Change Tracking and Transactions

#### Change Tracking

- EF Core tracks changes made to entities and automatically generates SQL commands to persist these changes to the database.

```csharp
var product = dbContext.Products.FirstOrDefault();
product.Price = 29.99;
dbContext.SaveChanges(); // Generates UPDATE statement
```

#### Transactions

- Use transactions to ensure data consistency across multiple operations.

```csharp
using (var transaction = dbContext.Database.BeginTransaction())
{
    try
    {
        // Perform multiple operations
        dbContext.SaveChanges();
        transaction.Commit();
    }
    catch (Exception)
    {
        transaction.Rollback();
    }
}
```

### 4. Database Migrations

#### Code-First Migrations

- EF Core supports code-first migrations for creating and managing database schema based on changes in the domain model.

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### 5. Advanced Mapping

#### Complex Types

- Map complex types to database columns.

```csharp
public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}

public class User
{
    public Address Address { get; set; }
}
```

#### Table-Per-Hierarchy (TPH) Inheritance

- Use inheritance to map a class hierarchy to a single database table.

```csharp
public abstract class Animal
{
    public int Id { get; set; }
    public string Name { get; set; }
}

public class Dog : Animal
{
    public string Breed { get; set; }
}

public class Cat : Animal
{
    public string Color { get; set; }
}
```

### 6. Database Providers

#### Multiple Database Providers

- EF Core supports multiple database providers including SQL Server, PostgreSQL, MySQL, SQLite, and more.

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer(connectionString));
```

These are some of the advanced features of Entity Framework Core in .NET Core C#. By leveraging these features, you can efficiently work with databases and build robust and scalable applications. Let me know if you need further clarification or more examples!