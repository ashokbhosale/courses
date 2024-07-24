Implementing authentication and authorization is crucial for securing your applications. In .NET Core, you can achieve this using various mechanisms such as Identity, JWT (JSON Web Tokens), and custom policies. Let's see how to implement authentication and authorization using these mechanisms with examples.

### 1. Using Identity:

Identity is a membership system that adds login functionality to your application. It includes user registration, login, password management, and role-based authorization.

#### Example:

1. Install the necessary NuGet packages:

```bash
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

2. Configure Identity in `Startup.cs`:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddControllersWithViews();
}
```

3. Use Identity in your controllers:

```csharp
[Authorize]
public class MyController : Controller
{
    // Your actions
}
```

### 2. Using JWT:

JWT is a compact, URL-safe means of representing claims to be transferred between two parties. It can be used for authentication and authorization in web applications.

#### Example:

1. Install the necessary NuGet packages:

```bash
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```

2. Configure JWT authentication in `Startup.cs`:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters = new TokenValidationParameters
            {
                ValidateIssuer = true,
                ValidateAudience = true,
                ValidateLifetime = true,
                ValidateIssuerSigningKey = true,
                ValidIssuer = "your_issuer",
                ValidAudience = "your_audience",
                IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes("your_secret_key"))
            };
        });

    services.AddControllers();
}
```

3. Protect your endpoints with `[Authorize]` attribute:

```csharp
[Authorize]
[ApiController]
public class MyController : ControllerBase
{
    // Your actions
}
```

### 3. Using Custom Policies:

You can create custom authorization policies to define complex access rules for your application.

#### Example:

1. Define a custom policy in `Startup.cs`:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddAuthorization(options =>
    {
        options.AddPolicy("AdminOnly", policy =>
            policy.RequireRole("Admin"));
    });

    // Other configurations
}
```

2. Use the custom policy in your controllers:

```csharp
[Authorize(Policy = "AdminOnly")]
public class AdminController : Controller
{
    // Your actions accessible only to users with "Admin" role
}
```

These are the basic examples of implementing authentication and authorization mechanisms in .NET Core applications using Identity, JWT, and custom policies. Depending on your application's requirements, you may need to customize these approaches further.