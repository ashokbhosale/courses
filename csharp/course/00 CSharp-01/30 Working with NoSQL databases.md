Working with NoSQL databases in .NET Core C# involves using libraries and frameworks that provide support for specific NoSQL databases. While Entity Framework Core is commonly used for relational databases, several options are available for working with NoSQL databases. Here are some approaches for working with NoSQL databases in .NET Core C#:

### 1. Using Native Drivers

Many NoSQL databases provide official or community-supported .NET Core drivers that allow you to interact with the database directly using the native protocol.

- **MongoDB**: MongoDB offers the official MongoDB .NET Driver, which supports .NET Core and allows you to perform CRUD operations, query data, and more.

```csharp
using MongoDB.Driver;

var client = new MongoClient("mongodb://localhost:27017");
var database = client.GetDatabase("mydatabase");
var collection = database.GetCollection<BsonDocument>("mycollection");

var document = new BsonDocument
{
    { "name", "John" },
    { "age", 30 }
};

await collection.InsertOneAsync(document);
```

- **Redis**: Redis provides the StackExchange.Redis library, a high-performance .NET Core Redis client. It allows you to connect to a Redis server and perform operations like storing and retrieving data.

```csharp
using StackExchange.Redis;

var redis = ConnectionMultiplexer.Connect("localhost:6379");
var database = redis.GetDatabase();

await database.StringSetAsync("key", "value");
var value = await database.StringGetAsync("key");
```

### 2. Using Object-Document Mappers (ODM)

Object-Document Mappers are libraries that provide a higher-level abstraction over NoSQL databases, similar to ORMs for relational databases. They allow you to work with NoSQL databases using familiar object-oriented paradigms.

- **MongoDB**: For MongoDB, you can use libraries like MongoDB.Entities or MongoDB.Driver.Linq, which provide LINQ support for MongoDB queries.

```csharp
using MongoDB.Entities;

public class Person : Entity
{
    public string Name { get; set; }
    public int Age { get; set; }
}

var john = new Person { Name = "John", Age = 30 };
john.Save();
```

### 3. Using Abstraction Layers

Some libraries provide an abstraction layer over different NoSQL databases, allowing you to switch between databases without changing your code significantly.

- **Cosmos DB**: Azure Cosmos DB is a globally distributed, multi-model database service. The Microsoft.Azure.Cosmos SDK provides a unified API for working with Cosmos DB's SQL, MongoDB, Cassandra, Gremlin, and Table APIs.

```csharp
using Microsoft.Azure.Cosmos;

var cosmosClient = new CosmosClient("connectionString");
var container = cosmosClient.GetContainer("databaseId", "containerId");

var item = new { Name = "John", Age = 30 };
await container.CreateItemAsync(item);
```

### 4. Using Higher-Level Libraries

Some higher-level libraries provide support for specific NoSQL databases, offering additional features and abstractions.

- **RavenDB**: RavenDB is a document database that offers the RavenDB.Client library, which provides a client API for interacting with RavenDB.

```csharp
using Raven.Client.Documents;
using Raven.Client.Documents.Session;

var store = new DocumentStore
{
    Urls = new[] { "http://localhost:8080" },
    Database = "MyDatabase"
}.Initialize();

using (var session = store.OpenSession())
{
    var entity = new MyEntity { Name = "John" };
    session.Store(entity);
    session.SaveChanges();
}
```

These are some of the approaches for working with NoSQL databases in .NET Core C#. Depending on your requirements and preferences, you can choose the approach that best fits your application's needs. Let me know if you need further clarification or more examples!