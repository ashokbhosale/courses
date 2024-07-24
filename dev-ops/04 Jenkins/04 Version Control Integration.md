Integrating Jenkins with Git repositories and setting up automatic builds triggered by code changes is a fundamental part of a CI/CD pipeline. Below are the steps to achieve this integration:

**Prerequisites:**
- Jenkins server set up and running.
- Git client installed on the Jenkins server.
- A Git repository (e.g., on GitHub, GitLab, Bitbucket, or a self-hosted Git server).

**Steps to Integrate Jenkins with Git and Trigger Builds on Code Changes:**

1. **Install Required Plugins**:
   Before you can work with Git repositories in Jenkins, you may need to install some plugins. If you haven't already installed them during your initial Jenkins setup, follow these steps:

   - Log in to Jenkins.
   - Click on "Manage Jenkins" in the left-hand menu.
   - Select "Manage Plugins."
   - Go to the "Available" tab and search for "Git" in the filter field.
   - Check the box next to the "Git Plugin" and any other relevant Git-related plugins you may need (e.g., "GitHub plugin" for GitHub integration).
   - Click "Download now and install after restart."
   - Jenkins will download and install the selected plugins. After the installation, Jenkins will prompt you to restart.

2. **Configure Global Git Settings**:

   - After Jenkins restarts, go back to "Manage Jenkins" and select "Global Tool Configuration."
   - Under the "Git" section, enter the name and path to your Git executable. Typically, Jenkins can auto-detect Git, but you can specify the path manually if needed.

3. **Create a Jenkins Job**:
   If you haven't already created a Jenkins job for building and testing your code (as discussed in the previous response), create one as needed.

4. **Set Up Webhooks or Polling**:
   You can trigger Jenkins builds in response to code changes in your Git repository using one of the following methods:

   a. **Webhooks (Recommended)**:
      - Webhooks allow your Git repository to notify Jenkins of code changes automatically. To set up a webhook, you'll need to go to your Git repository hosting platform (e.g., GitHub, GitLab, Bitbucket) and add a webhook pointing to your Jenkins server. You will typically provide the Jenkins job's URL as the webhook payload URL.
   
   b. **Polling**:
      - You can configure Jenkins to periodically poll your Git repository for changes. This is less efficient than using webhooks but may be necessary in certain environments where webhooks are not available.
      - In your Jenkins job configuration, under the "Build Triggers" section, select "Poll SCM" and specify a schedule (e.g., `* * * * *` to check every minute). Jenkins will check the Git repository for changes at the specified interval.

5. **Configure Your Jenkins Job**:
   In your Jenkins job configuration:

   - Ensure that you've configured the source code management section to connect to your Git repository. Select the appropriate Git option (e.g., "Git" or "GitHub").
   - Provide the Git repository URL.
   - Configure any additional settings, such as the branch to build or specific Git credentials.

6. **Save and Test Your Configuration**:
   Save your Jenkins job configuration. You can manually trigger a build to ensure that the integration is working as expected.

7. **Test Automatic Builds**:
   Make a code change in your Git repository and push it. If you've set up webhooks, Jenkins should automatically trigger a build in response to the code change. If you're using polling, Jenkins will eventually pick up the changes according to your schedule.

By following these steps, Jenkins will be integrated with your Git repository, and builds will be automatically triggered upon code changes, allowing you to implement continuous integration in your development workflow.