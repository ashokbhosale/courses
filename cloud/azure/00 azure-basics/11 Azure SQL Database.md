Setting up and managing relational databases in the cloud using Azure SQL Database provides a scalable, secure, and fully managed platform for your data. Here's a guide on how to set up and manage Azure SQL Database:

1. **Create an Azure SQL Database**:
   - Navigate to the Azure Portal.
   - Click on "Create a resource" and search for "SQL Database."
   - Select "SQL Database" from the list of services.
   - Fill in the required details such as name, subscription, resource group, and region.
   - Choose the deployment option (single database, elastic pool) and performance tier (basic, standard, premium).
   - Configure additional settings such as compute and storage resources, collation, and backup retention.
   - Click on "Review + create" and then "Create" to provision the SQL Database.

2. **Connect to the Database**:
   - Once the SQL Database is created, navigate to it in the Azure Portal.
   - Go to the "Connection strings" tab to retrieve the connection string for connecting to the database from your application.
   - You can use tools like SQL Server Management Studio (SSMS), Azure Data Studio, or the Azure Portal's Query Editor to connect to and manage the database.

3. **Manage Database Objects**:
   - Create tables, views, stored procedures, functions, and other database objects using SQL scripts or graphical tools.
   - You can manage database objects directly in the Azure Portal or using client tools like SSMS or Azure Data Studio.

4. **Configure Security**:
   - Secure access to your Azure SQL Database by configuring firewall rules to allow access from specific IP addresses or Azure services.
   - Implement authentication and authorization using Azure Active Directory (Azure AD), SQL authentication, or Azure AD Integrated authentication.
   - Apply role-based access control (RBAC) to control access to database resources and data.

5. **Monitor Performance and Health**:
   - Monitor the performance and health of your Azure SQL Database using Azure Monitor and Query Performance Insights.
   - Monitor metrics such as CPU usage, storage usage, throughput, and query performance to identify bottlenecks and optimize performance.
   - Set up alerts to notify you when certain conditions are met, such as high CPU utilization or long-running queries.

6. **Backup and Restore**:
   - Configure automated backups and retention policies to ensure data durability and compliance.
   - You can perform point-in-time restores or restore to a specific transaction using automated backups.

7. **Scale Resources**:
   - Scale compute and storage resources dynamically based on workload demands.
   - You can scale up or down the performance tier (e.g., from standard to premium) or scale out with read replicas or sharding.

By following these steps, you can set up and manage relational databases in the cloud using Azure SQL Database, leveraging its scalability, reliability, and built-in management capabilities.