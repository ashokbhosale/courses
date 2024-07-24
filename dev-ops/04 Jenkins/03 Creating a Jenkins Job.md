Creating a basic Jenkins job for building and testing code involves several steps. In this example, I'll guide you through creating a simple Jenkins job to build and test a sample Java application. You can adapt this process for your specific programming language and build tools.

**Prerequisites:**
- Jenkins server set up and running.
- Git installed on the Jenkins server.
- Java Development Kit (JDK) installed on the Jenkins server.

Here are the steps to create a basic Jenkins job for building and testing code:

1. **Log in to Jenkins**: Open your web browser and navigate to the Jenkins web interface by entering `http://your-server-IP:8080` (replace with your Jenkins server's URL). Log in with your Jenkins admin credentials.

2. **Create a New Jenkins Job**:

   - Click on "New Item" on the Jenkins dashboard.
   - Enter a name for your job (e.g., "Build and Test MyApp").
   - Select the "Freestyle project" option.
   - Click "OK" to create the job.

3. **Configure the Jenkins Job**:

   a. **General Settings**:
   
      - You can specify a description for your job.
      
   b. **Source Code Management**:
   
      - Choose the version control system you are using (e.g., Git).
      - Provide the repository URL and specify the branch to build.

   c. **Build**:
   
      - Select "Add build step" and choose the appropriate build tool for your project. For a Java project, you can use "Execute shell" (for Unix-like systems) or "Execute Windows batch command" (for Windows).
      - In the build step, you can define the commands to build your code. For example, if you're using Maven for a Java project, you can enter something like:
      
        ```bash
        cd /path/to/your/project
        mvn clean package
        ```
   
   d. **Post-build Actions**:
   
      - Select "Add post-build action" and choose "Publish JUnit test result report."
      - In the "Test report XMLs" field, enter the path to your test results. For example, if you're using JUnit, the path might be `**/target/surefire-reports/*.xml`.

4. **Save the Jenkins Job Configuration**: Click the "Save" button to save the job configuration.

5. **Build the Jenkins Job**:

   - On the Jenkins dashboard, find your job and click "Build Now" to manually trigger the job.
   - You can also set up automatic builds by configuring a trigger, such as polling the repository for changes or setting up webhooks.

6. **View Build Results**:

   - Once the job is triggered, you can monitor the build progress by clicking on your job and then selecting the build number under the "Build History" section.
   - You can view the console output to see the build and test results.

This is a basic example of a Jenkins job for building and testing code. You can extend and customize this job to fit the specific requirements of your project, including configuring additional build tools, integrating with other testing frameworks, and setting up deployment steps as part of your CI/CD pipeline.