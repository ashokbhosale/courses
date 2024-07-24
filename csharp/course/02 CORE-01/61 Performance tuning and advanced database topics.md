Performance tuning and advanced database topics are essential for optimizing the performance and scalability of .NET Core C# applications that interact with databases. Here are some techniques and examples:

### 1. Database Indexing:

Proper indexing improves query performance by reducing the number of rows that need to be scanned.

#### Example:

```sql
CREATE INDEX IX_Product_Name ON Products (Name);
```

### 2. Query Optimization:

Optimize SQL queries by analyzing execution plans, using appropriate join types, and minimizing unnecessary operations.

#### Example:

```sql
SELECT p.Name, c.CategoryName
FROM Products p
INNER JOIN Categories c ON p.CategoryId = c.Id
WHERE p.Price > 100;
```

### 3. Connection Pooling:

Use connection pooling to reduce the overhead of creating and destroying database connections.

#### Example:

In your .NET Core application's connection string, enable connection pooling:

```csharp
"ConnectionStrings": {
    "DefaultConnection": "Server=myServerAddress;Database=myDataBase;User Id=myUsername;Password=myPassword;Pooling=true;"
}
```

### 4. Asynchronous Database Operations:

Use asynchronous database operations to improve scalability and responsiveness by freeing up threads while waiting for database queries to complete.

#### Example:

```csharp
public async Task<IEnumerable<Product>> GetProductsAsync()
{
    using (var connection = new SqlConnection(_connectionString))
    {
        await connection.OpenAsync();
        var query = "SELECT * FROM Products";
        return await connection.QueryAsync<Product>(query);
    }
}
```

### 5. Data Caching:

Cache frequently accessed data in memory to reduce database load and improve response times.

#### Example:

```csharp
public async Task<IEnumerable<Product>> GetProductsAsync()
{
    var key = "Products";
    var cachedProducts = await _cache.GetOrCreateAsync(key, async entry =>
    {
        entry.AbsoluteExpirationRelativeToNow = TimeSpan.FromMinutes(10);
        return await _repository.GetProductsAsync();
    });

    return cachedProducts;
}
```

### 6. Stored Procedures:

Use stored procedures for complex database operations to leverage precompiled execution plans and reduce network traffic.

#### Example:

```sql
CREATE PROCEDURE GetProductsByCategory
    @CategoryId INT
AS
BEGIN
    SELECT * FROM Products WHERE CategoryId = @CategoryId;
END;
```

### Conclusion:

Performance tuning and advanced database topics are critical for optimizing the performance and scalability of .NET Core C# applications. By applying techniques like database indexing, query optimization, connection pooling, asynchronous database operations, data caching, and stored procedures, you can improve the efficiency of database interactions and enhance overall application performance. Continuously monitor and fine-tune database performance to ensure optimal performance as your application scales.