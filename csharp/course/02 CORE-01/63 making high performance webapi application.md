Building a high-performance Web API application with .NET Core C# involves optimizing various aspects such as request processing, database access, caching, and more. Here's an example of how to build a high-performance Web API application using .NET Core:

### 1. Use Async/Await for Asynchronous Operations:

Utilize asynchronous programming with async/await to improve scalability and responsiveness by freeing up threads during I/O-bound operations.

#### Example:

```csharp
[HttpGet]
public async Task<ActionResult<IEnumerable<Product>>> GetProducts()
{
    var products = await _productService.GetProductsAsync();
    return Ok(products);
}
```

### 2. Implement Response Caching:

Cache frequently requested data at the API level to reduce database load and improve response times for subsequent requests.

#### Example:

```csharp
[HttpGet]
[ResponseCache(Duration = 60)] // Cache response for 60 seconds
public ActionResult<IEnumerable<Product>> GetProducts()
{
    var products = _productService.GetProducts();
    return Ok(products);
}
```

### 3. Optimize Database Queries:

Optimize database queries by using proper indexing, minimizing the number of queries, and fetching only the required data.

#### Example:

```csharp
public async Task<IEnumerable<Product>> GetProductsAsync()
{
    return await _dbContext.Products
                            .Include(p => p.Category)
                            .ToListAsync();
}
```

### 4. Use Dependency Injection:

Leverage dependency injection to manage dependencies and improve testability, maintainability, and performance.

#### Example:

```csharp
public class ProductService : IProductService
{
    private readonly ApplicationDbContext _dbContext;

    public ProductService(ApplicationDbContext dbContext)
    {
        _dbContext = dbContext;
    }

    // Service methods
}
```

### 5. Enable Compression:

Enable response compression to reduce bandwidth usage and improve latency for clients with limited bandwidth.

#### Example:

In Startup.cs:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCompression();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCompression();
}
```

### 6. Configure Logging and Monitoring:

Implement logging and monitoring to identify performance bottlenecks and optimize application behavior.

#### Example:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env, ILoggerFactory loggerFactory)
{
    loggerFactory.AddFile("Logs/mylog-{Date}.txt");

    // Other configurations
}
```

### 7. Implement Caching Mechanisms:

Implement in-memory caching or distributed caching to store frequently accessed data and reduce latency.

#### Example:

```csharp
public async Task<IEnumerable<Product>> GetProductsAsync()
{
    var cacheKey = "Products";
    var cachedProducts = await _cache.GetOrCreateAsync(cacheKey, async entry =>
    {
        entry.AbsoluteExpirationRelativeToNow = TimeSpan.FromMinutes(10);
        return await _dbContext.Products.ToListAsync();
    });

    return cachedProducts;
}
```

### Conclusion:

By following these best practices and examples, you can build a high-performance Web API application using .NET Core C#. Remember to profile and monitor your application regularly to identify performance bottlenecks and optimize critical areas. Additionally, consider leveraging cloud services, distributed caching, and load balancing for further scalability and performance improvements as your application grows.