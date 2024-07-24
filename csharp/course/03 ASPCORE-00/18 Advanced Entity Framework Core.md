Entity Framework Core (EF Core) is a powerful and flexible Object-Relational Mapping (ORM) framework for .NET applications. In addition to basic CRUD operations, EF Core offers advanced features for working with databases, including complex queries, database views, and executing raw SQL. Let's dive deeper into these advanced EF Core features:

### Complex Queries:

EF Core allows you to construct complex queries using the LINQ (Language Integrated Query) syntax. You can perform various operations such as filtering, sorting, grouping, and aggregating data in a strongly typed and type-safe manner. Here's an example of a complex query using LINQ:

```csharp
var highValueProducts = context.Products
    .Where(p => p.Price > 100)
    .OrderBy(p => p.Name)
    .Select(p => new { p.Id, p.Name, p.Price })
    .ToList();
```

In this example, we're filtering products with a price higher than 100, ordering them by name, and selecting specific properties.

### Database Views:

Database views are virtual tables that allow you to define precomputed queries in your database schema. EF Core supports mapping to database views, treating them like regular entities. To map an entity to a database view, you can use the `ToView` method in your DbContext:

```csharp
public class ApplicationDbContext : DbContext
{
    public DbSet<ProductsView> ProductsView { get; set; }

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.Entity<ProductsView>().ToView("ProductsView");
    }
}
```

In this example, `ProductsView` represents a database view named "ProductsView." You can query this view as you would a regular entity.

### Raw SQL Queries:

Sometimes, you may need to execute raw SQL queries to perform operations that are not easily expressible with LINQ or to take advantage of database-specific features. EF Core allows you to execute raw SQL queries using the `FromSqlRaw` or `FromSqlInterpolated` methods:

```csharp
var products = context.Products.FromSqlRaw("SELECT * FROM Products WHERE Price > {0}", 100).ToList();
```

The `FromSqlRaw` method allows you to execute parameterized SQL queries safely.

### Stored Procedures:

EF Core can also map to stored procedures, allowing you to call database functions using LINQ. You can create a mapped function in your DbContext like this:

```csharp
[DbFunction("dbo", "GetProductsByPrice")]
public static IQueryable<Product> GetProductsByPrice(ApplicationDbContext context, decimal price)
{
    var priceParameter = new SqlParameter("price", price);
    return context.Products.FromSqlRaw("EXEC GetProductsByPrice @price", priceParameter);
}
```

Then, you can use this function to execute a stored procedure in your LINQ queries:

```csharp
var expensiveProducts = context.GetProductsByPrice(100).ToList();
```

EF Core provides powerful tools for querying, mapping to views, and executing raw SQL, making it suitable for a wide range of database-related tasks in your ASP.NET Core applications. When using raw SQL or stored procedures, ensure you follow best practices to mitigate security and performance risks, such as SQL injection and query optimization.