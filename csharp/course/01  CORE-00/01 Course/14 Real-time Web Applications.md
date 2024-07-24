SignalR is a library in ASP.NET Core that enables real-time communication between the server and clients over WebSockets, Server-Sent Events (SSE), or Long Polling. It's commonly used for building features like live chat, notifications, real-time updates, and collaborative editing in web applications. Let's explore how to use SignalR to build real-time features in a .NET Core web application with an example.

### Example: Real-Time Chat Application using SignalR

1. Create a new ASP.NET Core web application:

```bash
dotnet new web -n RealTimeChatApp
cd RealTimeChatApp
```

2. Install SignalR NuGet package:

```bash
dotnet add package Microsoft.AspNetCore.SignalR
```

3. Create a SignalR hub:

Create a new class named `ChatHub.cs`:

```csharp
using Microsoft.AspNetCore.SignalR;
using System.Threading.Tasks;

namespace RealTimeChatApp
{
    public class ChatHub : Hub
    {
        public async Task SendMessage(string user, string message)
        {
            await Clients.All.SendAsync("ReceiveMessage", user, message);
        }
    }
}
```

4. Configure SignalR in `Startup.cs`:

```csharp
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

namespace RealTimeChatApp
{
    public class Startup
    {
        public void ConfigureServices(IServiceCollection services)
        {
            services.AddSignalR();
            services.AddControllersWithViews();
        }

        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }
            else
            {
                app.UseExceptionHandler("/Home/Error");
                app.UseHsts();
            }

            app.UseHttpsRedirection();
            app.UseStaticFiles();

            app.UseRouting();

            app.UseAuthorization();

            app.UseEndpoints(endpoints =>
            {
                endpoints.MapControllerRoute(
                    name: "default",
                    pattern: "{controller=Home}/{action=Index}/{id?}");
                endpoints.MapHub<ChatHub>("/chatHub");
            });
        }
    }
}
```

5. Create a simple HTML page for the chat client:

Create `Views/Home/Index.cshtml`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Real-Time Chat App</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script src="/lib/microsoft/signalr/dist/browser/signalr.min.js"></script>
</head>
<body>
    <div id="chatDiv">
        <input type="text" id="userInput" placeholder="Enter your name" />
        <input type="text" id="messageInput" placeholder="Enter message" />
        <button onclick="sendMessage()">Send</button>
        <ul id="messagesList"></ul>
    </div>

    <script>
        const connection = new signalR.HubConnectionBuilder()
            .withUrl("/chatHub")
            .build();

        connection.on("ReceiveMessage", function (user, message) {
            $('#messagesList').append('<li><strong>' + user + '</strong>: ' + message + '</li>');
        });

        connection.start().catch(err => console.error(err.toString()));

        function sendMessage() {
            var user = $('#userInput').val();
            var message = $('#messageInput').val();
            connection.invoke("SendMessage", user, message).catch(err => console.error(err.toString()));
        }
    </script>
</body>
</html>
```

6. Run the application:

```bash
dotnet run
```

Now, you can open multiple browser tabs and start chatting in real-time. Each message sent by a client will be immediately displayed to all connected clients.

This example demonstrates the basics of building a real-time chat application using SignalR in .NET Core. You can extend this further by adding features like user authentication, message persistence, typing indicators, and more.