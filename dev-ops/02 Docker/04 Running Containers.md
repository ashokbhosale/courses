Creating and running Docker containers from images is a fundamental aspect of Docker. Here are the basic steps to create and run Docker containers:

1. **Pull an Image**:
   - Before you can create a container, you need to have a Docker image. You can either build your own image using a Dockerfile or pull an existing image from a registry like Docker Hub.
   - To pull an image, you can use the `docker pull` command. For example, to pull the official Ubuntu image, you can run:
     ```bash
     docker pull ubuntu
     ```

2. **Run a Container**:
   - Once you have the image, you can run a container from it using the `docker run` command. For example, to run a basic Ubuntu container, use:
     ```bash
     docker run -it ubuntu
     ```
   - The `-it` flags allocate an interactive terminal, allowing you to interact with the container's shell.

3. **Interact with the Container**:
   - You are now inside the container. You can execute commands, install software, and make changes just as you would on a regular system.
   - For example, you can update the package list and install a text editor within the container:
     ```bash
     apt-get update
     apt-get install nano
     ```

4. **Exit the Container**:
   - To exit the container, type `exit` in the terminal, and it will return you to the host system.

5. **List Running Containers**:
   - You can check which containers are currently running using the `docker ps` command. To see all containers, including stopped ones, use `docker ps -a`.

6. **Stop a Container**:
   - If you want to stop a running container, you can use the `docker stop` command, followed by the container's name or ID. For example:
     ```bash
     docker stop <container_name_or_id>
     ```

7. **Remove a Container**:
   - To remove a stopped container, use the `docker rm` command, followed by the container's name or ID:
     ```bash
     docker rm <container_name_or_id>
     ```

8. **Run a Container in the Background**:
   - If you want to run a container in the background (detached mode), you can use the `-d` flag with `docker run`:
     ```bash
     docker run -d ubuntu
     ```

9. **View Container Logs**:
   - To view the logs of a running container, you can use the `docker logs` command followed by the container's name or ID:
     ```bash
     docker logs <container_name_or_id>
     ```

These are the basic steps to create, run, and manage Docker containers from images. Docker provides a wide range of options and flags to customize container behavior, networking, and more. Additionally, you can create your own Docker images using Dockerfiles and then use those images to run containers with your custom applications and configurations.