Performing CRUD (Create, Read, Update, Delete) operations with .NET Core involves interacting with a database to manipulate data. Here's a brief overview of how to perform CRUD operations using Entity Framework Core in .NET Core:

1. **Create Operation (Insert)**:
   - To create a new record in the database, you need to add a new entity object to the corresponding DbSet.
   - Use the `Add` method to add the entity to the DbSet, and then call `SaveChanges` to persist the changes to the database.

```csharp
using (var context = new YourDbContext())
{
    var newEntity = new YourEntity { /* Initialize properties */ };
    context.YourEntities.Add(newEntity);
    context.SaveChanges();
}
```

2. **Read Operation (Retrieve)**:
   - To retrieve data from the database, you can use LINQ queries to filter, project, and sort data.
   - Use methods like `ToList`, `FirstOrDefault`, `SingleOrDefault`, `Find`, or `Where` to fetch data from the DbSet.

```csharp
using (var context = new YourDbContext())
{
    var entities = context.YourEntities.ToList();
    var entity = context.YourEntities.FirstOrDefault(e => e.Id == entityId);
}
```

3. **Update Operation (Modify)**:
   - To update an existing record in the database, first retrieve the entity to be updated.
   - Modify its properties, and then call `SaveChanges` to persist the changes.

```csharp
using (var context = new YourDbContext())
{
    var entityToUpdate = context.YourEntities.Find(entityId);
    if (entityToUpdate != null)
    {
        entityToUpdate.Property1 = newValue1;
        entityToUpdate.Property2 = newValue2;
        // Update other properties as needed
        context.SaveChanges();
    }
}
```

4. **Delete Operation (Remove)**:
   - To delete a record from the database, first retrieve the entity to be deleted.
   - Use the `Remove` method to mark the entity for deletion, and then call `SaveChanges` to apply the deletion to the database.

```csharp
using (var context = new YourDbContext())
{
    var entityToDelete = context.YourEntities.Find(entityId);
    if (entityToDelete != null)
    {
        context.YourEntities.Remove(entityToDelete);
        context.SaveChanges();
    }
}
```

Remember to handle exceptions appropriately when performing CRUD operations, especially when dealing with database connectivity issues or validation errors. Additionally, consider using asynchronous methods (`SaveChangesAsync`, `ToListAsync`, etc.) for better performance in asynchronous applications.