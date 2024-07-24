Entity Framework Core (EF Core) is a lightweight, extensible, and cross-platform ORM (Object-Relational Mapper) framework provided by Microsoft. It allows developers to work with relational databases using .NET Core and C#. EF Core simplifies the task of database access, entity modeling, and data migrations by providing a set of powerful features and APIs. Let's dive into some of the key concepts and see examples of how to use EF Core with .NET Core C#.

### 1. Installation:

First, you need to install the necessary NuGet packages:

```bash
dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

### 2. Define Entities:

Entities are classes that represent tables in your database. Define your entities like this:

```csharp
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

### 3. Define DbContext:

DbContext represents your database session and provides APIs to query and save data. Create a class inheriting from DbContext:

```csharp
public class AppDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer("your_connection_string_here");
    }
}
```

### 4. Perform CRUD Operations:

Now, you can use your DbContext to perform CRUD operations:

```csharp
using (var context = new AppDbContext())
{
    // Add new product
    var newProduct = new Product { Name = "Laptop", Price = 999.99 };
    context.Products.Add(newProduct);
    context.SaveChanges();

    // Query products
    var products = context.Products.ToList();

    // Update product
    var productToUpdate = context.Products.FirstOrDefault(p => p.Name == "Laptop");
    if (productToUpdate != null)
    {
        productToUpdate.Price = 1099.99;
        context.SaveChanges();
    }

    // Delete product
    var productToDelete = context.Products.FirstOrDefault(p => p.Name == "Laptop");
    if (productToDelete != null)
    {
        context.Products.Remove(productToDelete);
        context.SaveChanges();
    }
}
```

### 5. Data Migrations:

EF Core supports database migrations to keep your database schema in sync with your code. Use the following commands to create and apply migrations:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

This will create a migration script based on the changes in your DbContext and apply them to the database.

That's a basic overview of using EF Core with .NET Core C#. You can explore more advanced features like querying, relationships, and performance optimization as you delve deeper into EF Core.