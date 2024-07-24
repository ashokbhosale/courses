Networking in Docker is a critical aspect of containerization, as it allows containers to communicate with each other and the outside world. Docker provides a flexible and robust networking system that enables containers to be connected in various ways. Here's an overview of networking in Docker and how to connect containers:

**Docker Networking Concepts**:

1. **Docker Bridge Network**:
   - By default, when Docker is installed, it creates a bridge network named `bridge`. Containers attached to this network can communicate with each other using container names as hostnames.
   - The bridge network provides NAT (Network Address Translation) for outgoing traffic, allowing containers to reach external networks.

2. **User-Defined Bridge Networks**:
   - Docker allows you to create user-defined bridge networks. Containers connected to the same user-defined network can communicate with each other.
   - User-defined bridge networks offer better isolation and control compared to the default `bridge` network.

3. **Host Network**:
   - Containers can be connected to the host's network namespace using the `--network host` flag. This allows a container to share the network stack with the host, effectively making it a part of the host's network.

4. **Overlay Network**:
   - Overlay networks are used in Docker swarm mode to enable container communication across multiple Docker hosts. These networks are ideal for orchestrating multi-host services.

5. **MacVLAN Network**:
   - MacVLAN allows you to assign a MAC address to a container, making it appear as if it's directly attached to a physical network. It's useful for scenarios where containers need to have unique IP addresses on the host network.

6. **Container DNS**:
   - Containers connected to the same network can typically use container names as hostnames to communicate. Docker provides internal DNS resolution for containers on the same network.

**Connecting Containers**:

To connect containers in Docker, you can use the following methods:

1. **Using the Same Bridge Network**:
   - When you create multiple containers, you can connect them to the same user-defined bridge network. They can communicate with each other using their container names as hostnames.

   ```bash
   # Create a user-defined bridge network
   docker network create my-network

   # Run containers and connect them to the same network
   docker run -d --network my-network --name container1 my-image1
   docker run -d --network my-network --name container2 my-image2
   ```

2. **Using Environment Variables**:
   - You can use environment variables to pass connection information between containers. For example, you might set an environment variable in one container with the IP address or hostname of another container.

   ```bash
   # Run a container and set an environment variable
   docker run -d --name container1 -e TARGET_CONTAINER_IP=<ip_of_container2> my-image1
   docker run -d --name container2 my-image2
   ```

3. **Using External Networks**:
   - If you want containers to communicate with each other over an external network, you can use the `--network` flag when running containers to connect them to the host network or an existing bridge network.

   ```bash
   # Run containers connected to the host network
   docker run -d --network host my-image1
   docker run -d --network host my-image2
   ```

Remember that Docker's built-in DNS resolution allows containers to use each other's names as hostnames when they are connected to the same network. This simplifies the process of container communication. Additionally, tools like Docker Compose make it even easier to define and manage networks when working with multiple containers in an application.