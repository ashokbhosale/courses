Performance optimization is crucial for ensuring that your .NET Core applications run efficiently, especially as they scale. Here are some common performance optimization techniques along with examples:

### 1. Caching:

Caching involves storing frequently accessed data in memory to reduce the need for repeated computations or database queries.

#### Example:

```csharp
using Microsoft.Extensions.Caching.Memory;
using System;

public class CacheExample
{
    private readonly IMemoryCache _cache;

    public CacheExample(IMemoryCache cache)
    {
        _cache = cache;
    }

    public string GetDataFromCache()
    {
        string data;
        if (!_cache.TryGetValue("cachedData", out data))
        {
            // Data not in cache, retrieve it from source
            data = GetDataFromSource();

            // Cache the data
            _cache.Set("cachedData", data, TimeSpan.FromMinutes(10));
        }

        return data;
    }

    private string GetDataFromSource()
    {
        // Simulate fetching data from a database or external service
        return "Cached data";
    }
}
```

### 2. Lazy Loading:

Lazy loading delays the initialization of an object until it's accessed for the first time, which can improve startup time and reduce memory usage.

#### Example:

```csharp
public class LazyLoadingExample
{
    private readonly Lazy<DataAccessService> _dataAccessService = new Lazy<DataAccessService>(() => new DataAccessService());

    public void UseDataAccessService()
    {
        // DataAccessService is initialized only when it's accessed for the first time
        DataAccessService dataAccess = _dataAccessService.Value;
        // Use dataAccess...
    }
}
```

### 3. Load Balancing:

Load balancing distributes incoming network traffic across multiple servers to ensure no single server is overloaded, thereby improving performance and reliability.

#### Example:

You can use a load balancing solution such as Kubernetes, Nginx, or Azure Load Balancer to distribute traffic among multiple instances of your application deployed across different servers or containers.

These are just a few examples of performance optimization techniques in .NET Core. Depending on your application's specific requirements and architecture, you may need to explore additional techniques such as asynchronous programming, database indexing, query optimization, and more to achieve optimal performance.