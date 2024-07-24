**Microservices Architecture:**

Microservices architecture is an architectural style where an application is divided into small, independently deployable services, each representing a specific business capability. These services communicate through well-defined APIs and can be developed, deployed, and scaled independently. Microservices architecture promotes flexibility, scalability, and resilience.

**Building Microservices with .NET Core and ASP.NET Core:**

.NET Core and ASP.NET Core are well-suited for building microservices due to their lightweight nature, cross-platform compatibility, and support for modern development practices.

```csharp
// Example of a simple microservice using ASP.NET Core
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapControllers();
        });
    }
}

[ApiController]
[Route("[controller]")]
public class HelloWorldController : ControllerBase
{
    [HttpGet]
    public ActionResult<string> Get()
    {
        return "Hello, World!";
    }
}
```

In this example, we have a simple microservice implemented using ASP.NET Core. The `HelloWorldController` exposes a single endpoint that returns a "Hello, World!" message.

**Service Discovery, Communication, and Orchestration:**

Service discovery, communication, and orchestration are essential aspects of microservices architecture.

For service discovery, tools like Consul or Eureka can be used to dynamically register and discover services in the environment.

Communication between microservices can be achieved using HTTP/REST APIs for synchronous communication or message brokers like RabbitMQ or Kafka for asynchronous communication.

Orchestration tools like Kubernetes or Docker Swarm help in deploying, managing, and scaling microservices in a distributed environment.

```yaml
# Example Kubernetes deployment file for a microservice
apiVersion: apps/v1
kind: Deployment
metadata:
  name: helloworld
spec:
  replicas: 3
  selector:
    matchLabels:
      app: helloworld
  template:
    metadata:
      labels:
        app: helloworld
    spec:
      containers:
      - name: helloworld
        image: helloworld:latest
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: helloworld
spec:
  selector:
    app: helloworld
  ports:
  - port: 80
    targetPort: 80
```

This Kubernetes deployment file defines a microservice called "helloworld" with three replicas and exposes it through a service for internal communication.