Versioning and documentation are crucial aspects of developing and maintaining APIs. Let's explore how to implement versioning and documentation in .NET Core C# with examples:

1. **Versioning**:
   Versioning allows you to introduce changes to your API while maintaining backward compatibility for existing clients. There are different approaches to versioning APIs, including URI-based versioning, query string-based versioning, header-based versioning, or media type-based versioning.

   Example of URI-based versioning in .NET Core C#:
   ```csharp
   services.AddApiVersioning(options =>
   {
       options.ReportApiVersions = true;
       options.AssumeDefaultVersionWhenUnspecified = true;
       options.DefaultApiVersion = new ApiVersion(1, 0);
       options.ApiVersionReader = new UrlSegmentApiVersionReader();
   });
   ```

   In this example:
   - ApiVersioning middleware is added to the ASP.NET Core pipeline.
   - The `ReportApiVersions` option enables reporting of API versions in response headers.
   - The `AssumeDefaultVersionWhenUnspecified` option specifies whether to use the default API version when no version is specified in the request.
   - The `DefaultApiVersion` option sets the default API version.
   - The `ApiVersionReader` specifies that the API version should be read from the URL segment.

2. **Documentation**:
   Documentation provides information about the usage and behavior of your API, making it easier for developers to understand and integrate with your API. Swagger/OpenAPI is a popular tool for documenting APIs, and Swashbuckle.AspNetCore is a library that integrates Swagger with ASP.NET Core.

   Example of integrating Swagger for API documentation in .NET Core C#:
   ```csharp
   services.AddSwaggerGen(c =>
   {
       c.SwaggerDoc("v1", new OpenApiInfo { Title = "My API", Version = "v1" });
   });
   ```

   In this example:
   - SwaggerGen middleware is added to the ASP.NET Core pipeline.
   - Swagger documentation is configured for API version "v1" with a title and version number.

   To enable Swagger UI to visualize and interact with the API documentation, add the Swagger middleware to the HTTP request pipeline:
   ```csharp
   app.UseSwagger();
   app.UseSwaggerUI(c =>
   {
       c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
   });
   ```

   This code adds Swagger UI middleware to the ASP.NET Core pipeline and specifies the endpoint for the API documentation JSON file.

By implementing versioning and documentation in your .NET Core C# API, you can effectively manage changes, ensure compatibility with existing clients, and provide clear and comprehensive documentation for developers who want to consume your API.