Entity Framework (EF) Core is an object-relational mapping (ORM) framework provided by Microsoft for .NET Core applications. It enables developers to work with relational databases using .NET objects and LINQ queries. Here are the basics of Entity Framework Core in C# .NET Core:

1. **Installation**:
   - Entity Framework Core is available as a NuGet package. You can install it using the NuGet Package Manager in Visual Studio or the .NET CLI.
   - Example: `dotnet add package Microsoft.EntityFrameworkCore.SqlServer`

2. **DbContext Class**:
   - In EF Core, the `DbContext` class is the main entry point for accessing a database.
   - It represents a session with the database and provides methods for querying and saving data.

3. **Entity Classes**:
   - Entity classes represent database tables or views. Each entity typically corresponds to a row in the database table.
   - Properties of the entity class represent columns in the database table.

4. **DbSet<TEntity>**:
   - The `DbSet<TEntity>` class represents a collection of entities of a specific type in the context of a database.
   - It allows you to query and perform CRUD operations on the corresponding database table.

5. **Configuration**:
   - EF Core allows you to configure entity mappings and relationships using the Fluent API or data annotations.
   - You can define primary keys, foreign keys, indexes, and other database-specific configurations.

6. **LINQ Queries**:
   - EF Core supports LINQ (Language Integrated Query) for querying data from the database.
   - You can use LINQ queries to filter, project, sort, and group data in a strongly-typed manner.

7. **CRUD Operations**:
   - Entity Framework Core provides methods for performing CRUD (Create, Read, Update, Delete) operations on entities:
     - `Add(entity)` to insert new records.
     - `Find(id)` or LINQ queries to retrieve records.
     - `Update(entity)` to update existing records.
     - `Remove(entity)` to delete records.

8. **Migrations**:
   - EF Core Migrations enable you to manage changes to the database schema over time.
   - You can create, apply, and revert migrations to keep the database schema in sync with the application's data model.

9. **Database Providers**:
   - EF Core supports various database providers such as SQL Server, MySQL, PostgreSQL, SQLite, etc.
   - You can specify the database provider in the DbContext configuration.

10. **DbContext Lifecycle**:
    - The `DbContext` instance should be created per request or per operation and should be disposed of after use to release resources.

Example of a simple DbContext class:

```csharp
using Microsoft.EntityFrameworkCore;

public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer("YourConnectionString");
    }
}
```

Entity Framework Core simplifies data access in .NET Core applications by providing a high-level abstraction over relational databases. It allows developers to focus on business logic rather than database interactions, thus improving productivity and maintainability.