Design patterns are fundamental to the design and architecture of frameworks and libraries, including those in the .NET Core ecosystem. Let's explore some design patterns commonly used in popular frameworks and libraries such as .NET Framework, ASP.NET Core, and Entity Framework:

### 1. .NET Framework:

- **Singleton Pattern**: The Singleton pattern is often used in the ConfigurationManager class to provide access to configuration settings throughout the application.
  
- **Factory Method Pattern**: In the .NET Framework, the IFormatProvider interface is a good example of the Factory Method pattern, where different implementations provide formatting for different cultures.

- **Observer Pattern**: Windows Forms and WPF applications in the .NET Framework utilize the Observer pattern extensively for event handling and data binding. Controls observe changes in data sources and update their state accordingly.

### 2. ASP.NET Core:

- **Dependency Injection (DI)**: ASP.NET Core heavily relies on the Dependency Injection pattern to manage dependencies between components. The built-in DI container provides services and injects them into controllers, middleware, and other components.

- **Middleware Pipeline**: The Middleware Pipeline in ASP.NET Core follows the Chain of Responsibility pattern. Each middleware component in the pipeline handles an HTTP request and can choose to pass it to the next component or terminate the pipeline.

- **Builder Pattern**: The options pattern in ASP.NET Core uses the Builder pattern to configure services and middleware during application startup. This allows for fluent configuration and customization of the application's behavior.

### 3. Entity Framework Core:

- **Unit of Work and Repository Patterns**: Entity Framework Core encourages the use of the Unit of Work and Repository patterns to manage database interactions. The DbContext acts as a Unit of Work, while DbSet<T> represents repositories for specific entity types.

- **Identity Map Pattern**: Entity Framework Core uses the Identity Map pattern to ensure that each entity retrieved from the database is represented by a single object instance within the DbContext. This helps maintain consistency and prevents duplicate entities.

- **Lazy Loading and Proxy Pattern**: Entity Framework Core supports lazy loading of related entities, which is implemented using proxy objects generated at runtime. This follows the Proxy pattern, where the proxy objects transparently intercept calls to load related data.

### Applying Design Patterns at a Larger Scale:

- **Architectural Patterns**: Beyond individual design patterns, frameworks and libraries often embody higher-level architectural patterns such as MVC (Model-View-Controller) in ASP.NET Core or MVVM (Model-View-ViewModel) in WPF applications.

- **Design Patterns in Framework Evolution**: Frameworks evolve over time, and design patterns play a crucial role in their evolution. For example, ASP.NET Core introduced the Middleware Pipeline as a refinement of traditional request processing pipelines, incorporating concepts from the Chain of Responsibility pattern.

- **Extensibility and Customization**: Frameworks are designed with extensibility in mind, allowing developers to customize behavior using design patterns such as Strategy or Extension Objects. For example, ASP.NET Core middleware can be customized or extended to add additional functionality to the request pipeline.

By understanding how design patterns are applied in frameworks and libraries, developers can gain insights into best practices and patterns commonly used in larger-scale software architecture. This knowledge enables them to design and implement robust, scalable, and maintainable applications in .NET Core C#.