Serverless computing platforms like AWS Lambda and Azure Functions have transformed the way applications are built and deployed. They allow developers to focus on writing code and let the platform handle infrastructure management. Here's what you need to know about serverless computing platforms for building event-driven applications:

**1. Event-Driven Architecture:**
   - Serverless platforms are ideal for event-driven architectures, where code is executed in response to events, such as HTTP requests, database changes, file uploads, or custom triggers.

**2. Key Concepts:**
   - Functions: Code in serverless platforms is organized into functions, which are stateless and ephemeral. Each function performs a specific task in response to an event.
   - Triggers: Events that trigger the execution of functions are called triggers. Triggers can be various types, including HTTP requests, database changes, or cloud storage events.
   - Scalability: Serverless platforms automatically scale the number of function instances based on the incoming events. You pay only for the compute time used during execution.

**3. Supported Languages:**
   - Serverless platforms typically support multiple programming languages, including JavaScript, Python, Java, C#, and more. Choose a language that best suits your application.

**4. AWS Lambda:**
   - AWS Lambda is Amazon Web Services' serverless platform. It supports a wide range of triggers and integrations with various AWS services.
   - You can create Lambda functions and deploy them as part of AWS serverless applications.

**5. Azure Functions:**
   - Azure Functions is Microsoft Azure's serverless platform. It offers similar event-driven capabilities and integrates well with Azure services.
   - You can write Azure Functions in various languages, including C#, Python, and JavaScript.

**6. Google Cloud Functions:**
   - Google Cloud Functions is Google Cloud's serverless platform. It enables event-driven application development using JavaScript, Python, and more.

**7. Event Sources:**
   - Serverless platforms can connect to various event sources, including API Gateway, S3 buckets, databases, message queues, and external HTTP endpoints.
   - You can configure functions to respond to these events by defining triggers and event handlers.

**8. Statelessness:**
   - Functions in serverless platforms are stateless, which means they don't retain information between executions. Data must be stored in external databases, caches, or storage systems.

**9. Auto Scaling:**
   - Serverless platforms automatically scale the number of function instances based on the volume of incoming events. This ensures that your application can handle varying workloads efficiently.

**10. Pricing Model:**
    - Serverless platforms follow a "pay-as-you-go" pricing model, where you are billed for the actual compute time consumed during function execution.
    - There is no need to provision or manage server resources, making it cost-effective for small and large applications.

**11. Cold Starts:**
    - Serverless platforms may have a short initialization time called a "cold start" when a function is invoked for the first time or after a period of inactivity. It's essential to account for cold starts in your application design.

**12. Development and Testing:**
    - Developing and testing serverless applications can be done locally or using provided testing environments. The development workflow differs from traditional monolithic applications.

**13. Integrations and Libraries:**
    - Serverless platforms provide integrations with various third-party services and libraries to facilitate common tasks, such as data storage, authentication, and communication.

**14. Use Cases:**
    - Serverless computing is suitable for various use cases, including web APIs, data processing, real-time image or video processing, IoT data handling, and more.

**15. Event Processing:** 
    - Serverless platforms are well-suited for event-driven applications, where events trigger automated actions or responses.

**16. Logging and Monitoring:**
    - Serverless platforms offer built-in logging and monitoring capabilities. You can track function execution, analyze performance, and troubleshoot issues.

Serverless computing platforms simplify application development by abstracting infrastructure management, offering automatic scaling, and allowing developers to focus on writing business logic. Learning how to use AWS Lambda, Azure Functions, or other serverless platforms can help you build efficient and cost-effective event-driven applications.