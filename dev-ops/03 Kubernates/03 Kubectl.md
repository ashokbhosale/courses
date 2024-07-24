`kubectl` is the command-line tool used to interact with a Kubernetes cluster. It allows you to perform various operations on the cluster, such as deploying applications, inspecting resources, managing pods, and much more. To use `kubectl`, you need to have a working Kubernetes cluster and `kubectl` installed on your local machine. Here are some common `kubectl` commands and operations:

**1. Cluster Information:**

- **Check Cluster Info**:
  ```bash
  kubectl cluster-info
  ```

- **View Cluster Nodes**:
  ```bash
  kubectl get nodes
  ```

**2. Managing Resources:**

- **List Resources**:
  ```bash
  kubectl get <resource>
  ```

  For example, to list pods, you can use `kubectl get pods`.

- **Describe Resource**:
  ```bash
  kubectl describe <resource> <resource_name>
  ```

  This command provides detailed information about a specific resource. For example, `kubectl describe pod my-pod`.

- **Create Resource**:
  ```bash
  kubectl create -f <resource_definition.yaml>
  ```

  This command creates a resource from a YAML or JSON configuration file.

- **Edit Resource**:
  ```bash
  kubectl edit <resource> <resource_name>
  ```

  Opens the resource definition in the default text editor for editing.

- **Delete Resource**:
  ```bash
  kubectl delete <resource> <resource_name>
  ```

- **Apply Changes to a Resource**:
  ```bash
  kubectl apply -f <resource_definition.yaml>
  ```

  Use this to update resources with a new configuration.

**3. Managing Pods:**

- **View Pod Logs**:
  ```bash
  kubectl logs <pod_name>
  ```

- **Execute a Command in a Pod**:
  ```bash
  kubectl exec -it <pod_name> -- <command>
  ```

  For example, to open a shell in a pod, you can use `kubectl exec -it my-pod -- /bin/sh`.

- **Port Forwarding**:
  ```bash
  kubectl port-forward <pod_name> <local_port>:<pod_port>
  ```

  Forward a port from your local machine to a pod for direct access.

**4. Managing Deployments:**

- **Scale Deployment**:
  ```bash
  kubectl scale --replicas=<num_replicas> deployment/<deployment_name>
  ```

- **Rolling Update**:
  ```bash
  kubectl set image deployment/<deployment_name> <container_name>=<new_image>
  ```

  Use this command to update a deployment to a new container image.

- **Deployment History**:
  ```bash
  kubectl rollout history deployment/<deployment_name>
  ```

- **Rollback Deployment**:
  ```bash
  kubectl rollout undo deployment/<deployment_name>
  ```

  Revert a deployment to a previous revision.

**5. Managing Services:**

- **Expose a Deployment as a Service**:
  ```bash
  kubectl expose deployment/<deployment_name> --type=NodePort --port=<port> --target-port=<target_port>
  ```

  This command exposes a deployment as a service.

- **View Service Endpoints**:
  ```bash
  kubectl get endpoints <service_name>
  ```

- **Edit Service**:
  ```bash
  kubectl edit svc/<service_name>
  ```

**6. Managing ConfigMaps and Secrets:**

- **Create ConfigMap from File**:
  ```bash
  kubectl create configmap <configmap_name> --from-file=<path/to/file>
  ```

- **Create Secret from Literal**:
  ```bash
  kubectl create secret generic <secret_name> --from-literal=key=value
  ```

- **View ConfigMaps and Secrets**:
  ```bash
  kubectl get configmaps
  kubectl get secrets
  ```

**7. Managing Namespaces:**

- **Create a Namespace**:
  ```bash
  kubectl create namespace <namespace_name>
  ```

- **Switch to a Different Namespace**:
  ```bash
  kubectl config set-context --current --namespace=<namespace_name>
  ```

**8. Other Useful Commands:**

- **Get Command Help**:
  ```bash
  kubectl --help
  ```

- **Autocomplete**:
  `kubectl` provides autocompletion for bash, zsh, and fish shells. You can enable it by running `kubectl completion <shell>`.

Remember to replace `<resource>`, `<resource_name>`, `<deployment_name>`, `<pod_name>`, `<configmap_name>`, `<secret_name>`, `<namespace_name>`, and other placeholders with the appropriate values for your cluster. `kubectl` provides extensive functionality for managing Kubernetes clusters, and this is just a subset of common operations. You can explore more by referring to the official Kubernetes documentation and other learning resources.