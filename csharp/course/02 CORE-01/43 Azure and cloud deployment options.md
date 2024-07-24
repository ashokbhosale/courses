Azure offers various cloud deployment options for .NET Core C# applications, allowing you to deploy, manage, and scale your applications with ease. Let's explore some common deployment options on Azure along with examples:

### 1. Azure App Service

Azure App Service is a fully managed platform for building, deploying, and scaling web apps. It supports multiple frameworks, including .NET Core.

#### Example:

Suppose you have a .NET Core web application named `MyAspNetCoreApp`. You can deploy it to Azure App Service using Azure CLI.

```bash
# Publish the .NET Core application
dotnet publish -c Release

# Deploy to Azure App Service
az webapp up --name my-aspnet-core-app --sku F1 --location <your-location> --os-type Windows --runtime "DOTNET|3.1"
```

Replace `<your-location>` with the Azure region where you want to deploy your app.

### 2. Azure Container Instances (ACI)

Azure Container Instances offer the fastest and simplest way to run a container in Azure, without managing any underlying infrastructure.

#### Example:

Suppose you have containerized your .NET Core application using Docker. You can deploy it to Azure Container Instances.

```bash
# Create a resource group
az group create --name myResourceGroup --location <your-location>

# Deploy container to Azure Container Instances
az container create --resource-group myResourceGroup --name mycontainer --image <your-container-image> --cpu 1 --memory 1 --registry-login-server <your-registry-server> --registry-username <your-username> --registry-password <your-password>
```

Replace `<your-container-image>`, `<your-registry-server>`, `<your-username>`, and `<your-password>` with your container image details.

### 3. Azure Kubernetes Service (AKS)

Azure Kubernetes Service simplifies deploying, managing, and scaling containerized applications using Kubernetes.

#### Example:

Assuming you have a Kubernetes cluster created in Azure AKS, you can deploy your .NET Core application to it.

```bash
# Apply Kubernetes deployment YAML
kubectl apply -f deployment.yaml
```

Here's a sample `deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-aspnet-core-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: my-aspnet-core-app
  template:
    metadata:
      labels:
        app: my-aspnet-core-app
    spec:
      containers:
      - name: my-aspnet-core-app
        image: <your-container-image>
        ports:
        - containerPort: 80
```

Replace `<your-container-image>` with your container image details.

### Conclusion

These are just a few examples of deployment options for .NET Core C# applications on Azure. Depending on your application requirements and preferences, you can choose the most suitable deployment option. Azure provides a wide range of services to meet various needs, from simple web apps to complex microservices architectures.