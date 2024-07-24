Setting up a Git server for centralized repositories typically involves using Git over SSH. Here's how to set up a centralized Git server on a Linux-based system:

### Prerequisites:

1. A Linux server (e.g., Ubuntu, CentOS) accessible via SSH.
2. Administrative access to the server.
3. Git installed on the server.
4. Git installed on your local machine.

### Steps to Set Up a Centralized Git Server:

1. **Create a User for Git:**

   It's a good practice to create a dedicated user for Git on your server to manage Git repositories and SSH access. Run the following command to create the user:

   ```bash
   sudo adduser git
   ```

   Follow the prompts to set a password and add any necessary user information.

2. **Generate SSH Key Pair for the Git User:**

   It's a common practice to set up SSH key authentication for the Git user. This provides secure access to the server. Follow these steps:

   - Log in as the Git user:

     ```bash
     su - git
     ```

   - Generate an SSH key pair for the Git user. Use the `ssh-keygen` command and follow the prompts:

     ```bash
     ssh-keygen
     ```

   - The public key should be located in `~/.ssh/id_rsa.pub`.

   - Copy the public key to the Git user's `~/.ssh/authorized_keys` file:

     ```bash
     mkdir -p ~/.ssh
     cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
     chmod 600 ~/.ssh/authorized_keys
     ```

   - Exit the Git user's shell:

     ```bash
     exit
     ```

3. **Create a Directory for Git Repositories:**

   Decide where you want to store Git repositories on your server. You can create a directory for this purpose. For example:

   ```bash
   sudo mkdir /var/git
   ```

4. **Initialize a Bare Git Repository:**

   To create a new centralized Git repository, navigate to the desired location (e.g., `/var/git`) and use the `git init --bare` command. For example:

   ```bash
   cd /var/git
   git init --bare myproject.git
   ```

   This command initializes a bare repository named `myproject.git`. Bare repositories are typically used for central repositories and do not have a working directory.

5. **Set Permissions:**

   Ensure that the Git user (`git`) has the necessary permissions to read and write to the repository directory:

   ```bash
   sudo chown -R git:git /var/git/myproject.git
   ```

6. **Enable Git over SSH:**

   On your local machine, you can now clone the centralized Git repository using the following URL:

   ```bash
   git clone git@your-server-ip:/var/git/myproject.git
   ```

   You'll be prompted for the Git user's password the first time you access the repository. After that, your SSH key will be used for authentication.

That's it! You've set up a centralized Git server using SSH. Your team can now collaborate by pushing and pulling code to and from the central server. Make sure to manage SSH keys and permissions carefully to maintain security.

Additionally, consider setting up Git hooks and access control to further customize the server's behavior and ensure project-specific workflows and security policies are followed.