Containerizing your .NET Core applications with Docker allows you to package your application and its dependencies into a lightweight, portable container, ensuring consistency across different environments and facilitating easy deployment and scalability. Let's see how to Dockerize a .NET Core application with an example.

### Example: Dockerizing a .NET Core Application

1. Create a new .NET Core application:

```bash
dotnet new webapi -n MyWebApi
cd MyWebApi
```

2. Add a Dockerfile to the root of your project:

```Dockerfile
# Use the official .NET Core SDK image
FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the project file and restore dependencies
COPY *.csproj ./
RUN dotnet restore

# Copy the remaining source code
COPY . ./

# Build the application
RUN dotnet publish -c Release -o out

# Use the official ASP.NET Core runtime image
FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS runtime

# Set the working directory in the container
WORKDIR /app

# Copy the published app from the build stage
COPY --from=build /app/out ./

# Expose port 80 to the outside world
EXPOSE 80

# Define the entry point for the application
ENTRYPOINT ["dotnet", "MyWebApi.dll"]
```

3. Build the Docker image:

```bash
docker build -t mywebapi .
```

4. Run the Docker container:

```bash
docker run -d -p 8080:80 --name mywebapicontainer mywebapi
```

Now, your .NET Core application is Dockerized and running in a container. You can deploy this container to any Docker-compatible platform, ensuring consistent behavior across different environments and enabling easy scaling and deployment.