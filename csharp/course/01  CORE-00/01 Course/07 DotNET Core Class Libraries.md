**.NET Core Class Libraries:**

.NET Core provides a rich set of class libraries that cover various functionalities required for developing applications. These libraries offer pre-built components and APIs for common tasks such as file I/O, data access, networking, cryptography, and more. Let's explore some of the key class libraries provided by .NET Core along with examples of their usage.

**1. System.IO Namespace (File I/O):**

The `System.IO` namespace contains types that enable reading and writing to files and streams.

```csharp
using System;
using System.IO;

class Program
{
    static void Main(string[] args)
    {
        // Write text to a file
        string filePath = "example.txt";
        File.WriteAllText(filePath, "Hello, .NET Core!");

        // Read text from a file
        string text = File.ReadAllText(filePath);
        Console.WriteLine("File content: " + text);
    }
}
```

**2. System.Data Namespace (Data Access):**

The `System.Data` namespace provides classes for working with data, including databases and data sources.

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main(string[] args)
    {
        // Connection string for SQL Server database
        string connectionString = "Server=localhost;Database=myDatabase;User Id=myUsername;Password=myPassword;";

        // Create a connection
        using (SqlConnection connection = new SqlConnection(connectionString))
        {
            // Open the connection
            connection.Open();

            // Execute a query
            string sql = "SELECT * FROM Employees";
            using (SqlCommand command = new SqlCommand(sql, connection))
            {
                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        Console.WriteLine($"{reader["FirstName"]} {reader["LastName"]}");
                    }
                }
            }
        }
    }
}
```

**3. System.Net Namespace (Networking):**

The `System.Net` namespace contains classes for networking operations such as sending and receiving data over the network.

```csharp
using System;
using System.Net;
using System.Net.Http;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        // Create an HttpClient instance
        using (HttpClient client = new HttpClient())
        {
            // Send a GET request
            HttpResponseMessage response = await client.GetAsync("https://api.example.com/data");

            // Check if the request was successful
            if (response.IsSuccessStatusCode)
            {
                // Read the response content
                string content = await response.Content.ReadAsStringAsync();
                Console.WriteLine("Response: " + content);
            }
            else
            {
                Console.WriteLine("Error: " + response.StatusCode);
            }
        }
    }
}
```

These are just a few examples of the built-in class libraries provided by .NET Core. By leveraging these libraries, you can efficiently handle various tasks in your .NET Core applications, reducing development time and effort.