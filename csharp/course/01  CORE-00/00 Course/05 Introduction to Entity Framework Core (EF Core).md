**Introduction to Entity Framework Core (EF Core):**

Entity Framework Core (EF Core) is a lightweight, extensible, and cross-platform version of the Entity Framework data access technology. It enables developers to work with relational databases using .NET objects and LINQ queries. EF Core provides a set of APIs for performing database operations such as querying, inserting, updating, and deleting data. It supports various database providers, including SQL Server, SQLite, MySQL, PostgreSQL, and more.

**Creating and Configuring Data Models with EF Core:**

To work with EF Core, you first need to define data models that represent your database entities. These models are typically classes that map to database tables. You can use data annotations or Fluent API to configure the mapping between classes and database tables, as well as define relationships between entities.

```csharp
// Example data model
public class Product
{
    public int ProductId { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}

// DbContext class
public class AppDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer("connection_string_here");
    }
}
```

**Performing CRUD Operations using EF Core:**

Once you've defined your data models and configured the DbContext, you can use EF Core to perform CRUD (Create, Read, Update, Delete) operations on your database entities.

```csharp
using (var context = new AppDbContext())
{
    // Create operation
    var newProduct = new Product { Name = "New Product", Price = 9.99 };
    context.Products.Add(newProduct);
    context.SaveChanges();

    // Read operation
    var products = context.Products.ToList();

    // Update operation
    var productToUpdate = context.Products.FirstOrDefault(p => p.ProductId == 1);
    if (productToUpdate != null)
    {
        productToUpdate.Price = 19.99;
        context.SaveChanges();
    }

    // Delete operation
    var productToDelete = context.Products.FirstOrDefault(p => p.ProductId == 1);
    if (productToDelete != null)
    {
        context.Products.Remove(productToDelete);
        context.SaveChanges();
    }
}
```

**Querying Data with LINQ:**

EF Core allows you to query data using LINQ (Language Integrated Query), which provides a unified syntax for querying various data sources, including databases. LINQ queries are type-safe and offer intellisense support.

```csharp
using (var context = new AppDbContext())
{
    var cheapProducts = context.Products.Where(p => p.Price < 10).ToList();
    var expensiveProducts = from p in context.Products where p.Price > 50 select p;
}
```

**Working with Migrations and Database Seeding:**

EF Core migrations enable you to evolve your database schema over time by applying incremental changes to it. Database seeding allows you to populate your database with initial data.

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

```csharp
// Seed data
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.Entity<Product>().HasData(
        new Product { ProductId = 1, Name = "Product 1", Price = 9.99 },
        new Product { ProductId = 2, Name = "Product 2", Price = 19.99 }
    );
}
```

These examples demonstrate the fundamentals of data access with Entity Framework Core in .NET Core applications, including defining data models, performing CRUD operations, querying data with LINQ, and working with migrations and database seeding.