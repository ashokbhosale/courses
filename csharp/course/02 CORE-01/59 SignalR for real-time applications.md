Sure, here's an example of how to implement SignalR in a .NET Core C# application for real-time communication:

### 1. Create a .NET Core Web Application:

Create a new .NET Core Web Application project in Visual Studio or using the .NET CLI.

### 2. Install SignalR Package:

Install the Microsoft.AspNetCore.SignalR package using NuGet Package Manager or the .NET CLI:

```bash
dotnet add package Microsoft.AspNetCore.SignalR
```

### 3. Define a SignalR Hub:

Create a SignalR hub that will handle real-time communication between clients and the server.

```csharp
using Microsoft.AspNetCore.SignalR;
using System.Threading.Tasks;

public class ChatHub : Hub
{
    public async Task SendMessage(string user, string message)
    {
        await Clients.All.SendAsync("ReceiveMessage", user, message);
    }
}
```

### 4. Configure SignalR in Startup.cs:

Configure SignalR services in the ConfigureServices method and enable the SignalR endpoint in the Configure method of Startup.cs.

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.Extensions.DependencyInjection;

public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSignalR();
    }

    public void Configure(IApplicationBuilder app)
    {
        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapHub<ChatHub>("/chathub");
        });
    }
}
```

### 5. Client-Side Integration:

Implement client-side code to connect to the SignalR hub and handle real-time communication events.

```html
<!DOCTYPE html>
<html>
<head>
    <title>SignalR Chat</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/microsoft-signalr/5.0.0/signalr.min.js"></script>
</head>
<body>
    <input type="text" id="userInput" />
    <input type="text" id="messageInput" />
    <button onclick="sendMessage()">Send</button>
    <ul id="messagesList"></ul>

    <script>
        const connection = new signalR.HubConnectionBuilder()
            .withUrl("/chathub")
            .build();

        connection.start()
            .then(() => console.log("Connection established"))
            .catch(err => console.error(err.toString()));

        connection.on("ReceiveMessage", (user, message) => {
            const li = document.createElement("li");
            li.textContent = `${user}: ${message}`;
            document.getElementById("messagesList").appendChild(li);
        });

        function sendMessage() {
            const user = document.getElementById("userInput").value;
            const message = document.getElementById("messageInput").value;
            connection.invoke("SendMessage", user, message)
                .catch(err => console.error(err.toString()));
        }
    </script>
</body>
</html>
```

### 6. Run the Application:

Run the application and open multiple browser windows or tabs to see real-time communication in action.

### Conclusion:

This example demonstrates how to implement SignalR in a .NET Core C# application for real-time communication between clients and the server. SignalR simplifies the process of building real-time web applications and enables features like chat applications, live notifications, and collaborative editing. Experiment with SignalR to explore its full potential for real-time communication in your applications.