Records are a new reference type introduced in C# 9.0 and .NET 5.0 (which is part of .NET Core). They are immutable by default and provide value-based equality semantics. Records are useful for representing immutable data and are particularly handy for DTOs (Data Transfer Objects), data models, and similar scenarios where immutability and value equality are desired.

Here's how you can define and use records in .NET Core C#:

1. **Defining Records**:

   You define a record using the `record` keyword:

   ```csharp
   public record Person
   {
       public string FirstName { get; }
       public string LastName { get; }

       public Person(string firstName, string lastName)
       {
           FirstName = firstName;
           LastName = lastName;
       }
   }
   ```

   In this example, `Person` is a record with two properties: `FirstName` and `LastName`. Records automatically generate a constructor, `Equals` method, `GetHashCode` method, and `ToString` method based on the properties defined.

2. **Creating Instances**:

   You can create instances of records just like you would with classes:

   ```csharp
   var person = new Person("John", "Doe");
   ```

3. **Equality Comparison**:

   Records provide value-based equality semantics by default. Two records are considered equal if all their properties are equal:

   ```csharp
   var person1 = new Person("John", "Doe");
   var person2 = new Person("John", "Doe");

   Console.WriteLine(person1 == person2); // Output: True
   ```

4. **Immutable Properties**:

   Properties of records are read-only by default, making records immutable:

   ```csharp
   var person = new Person("John", "Doe");
   // person.FirstName = "Jane"; // Error: Cannot assign to 'FirstName' because it is read-only
   ```

5. **Deconstruction**:

   You can deconstruct records into their individual properties:

   ```csharp
   var (firstName, lastName) = person;
   Console.WriteLine($"First Name: {firstName}, Last Name: {lastName}");
   ```

6. **With-expressions**:

   Records support `with` expressions for creating new instances with modified values:

   ```csharp
   var modifiedPerson = person with { LastName = "Smith" };
   ```

Records simplify code by reducing boilerplate for creating immutable types and providing value-based equality semantics out of the box. They are especially beneficial in scenarios where immutability, value equality, and concise syntax are desired.