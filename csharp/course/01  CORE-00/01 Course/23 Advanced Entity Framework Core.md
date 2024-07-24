Advanced Entity Framework Core (EF Core) features allow you to handle complex scenarios, optimize performance, and manage database migrations effectively. Let's explore some of these advanced features with examples:

### 1. Complex Queries:

#### Example: Performing a complex query with EF Core using LINQ:

```csharp
using (var context = new YourDbContext())
{
    var result = context.Orders
        .Where(o => o.TotalAmount > 1000 && o.CustomerId == 1)
        .OrderByDescending(o => o.OrderDate)
        .Select(o => new
        {
            o.OrderId,
            o.OrderDate,
            o.TotalAmount,
            CustomerName = o.Customer.Name // Accessing related entities
        })
        .ToList();
}
```

### 2. Migrations:

#### Example: Creating and applying database migrations with EF Core:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### 3. Optimization Techniques:

#### Example: Optimizing database queries with EF Core using Include and ThenInclude:

```csharp
using (var context = new YourDbContext())
{
    var ordersWithDetails = context.Orders
        .Include(o => o.OrderDetails) // Eager loading
            .ThenInclude(od => od.Product) // Nested include
        .ToList();
}
```

#### Example: Using AsNoTracking to improve performance when retrieving read-only data:

```csharp
using (var context = new YourDbContext())
{
    var readOnlyOrders = context.Orders.AsNoTracking().ToList();
}
```

#### Example: Batch processing to improve performance when updating or deleting large datasets:

```csharp
using (var context = new YourDbContext())
{
    var ordersToDelete = context.Orders.Where(o => o.Status == "Cancelled").ToList();

    foreach (var order in ordersToDelete)
    {
        context.Orders.Remove(order);
    }

    context.SaveChanges();
}
```

These are just a few examples of how you can leverage advanced features in EF Core to handle complex scenarios, optimize performance, and manage database migrations effectively in your .NET Core applications. By mastering these techniques, you can build efficient and scalable data access layers for your applications.