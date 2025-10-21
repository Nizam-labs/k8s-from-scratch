## kubectl: The Command-Line Tool

kubectl is the primary command-line interface for interacting with your Kubernetes cluster. It allows you to run commands against the cluster to deploy applications, inspect and manage cluster resources, and view logs.

**General Command Syntax**

The general format of a kubectl command is:

kubectl &lt;command&gt; &lt;resource-type&gt; &lt;resource-name&gt; \[flags\]

**Configuration and Context**

| Command | Description | Example |
| --- | --- | --- |
| kubectl config get-contexts | Lists all contexts in your kubeconfig file. | kubectl config get-contexts |
| kubectl config use-context | Switches your current context to a different cluster. | kubectl config use-context minikube |
| kubectl cluster-info | Displays information about the cluster's control plane. | kubectl cluster-info |
| kubectl version | Shows the version of kubectl and the cluster's API server. | kubectl version --short |

**Resource Creation and Management**

| Command | Description | Example |
| --- | --- | --- |
| kubectl apply -f | Creates or updates resources from a manifest file. | kubectl apply -f deployment.yaml |
| kubectl create | Creates resources imperatively. | kubectl create deployment my-nginx --image=nginx |
| kubectl delete | Deletes resources by name or file. | kubectl delete pod my-pod |
| kubectl edit | Edits a resource definition in your default text editor. | kubectl edit service my-service |

**Resource Inspection**

| Command | Description | Example |
| --- | --- | --- |
| kubectl get | Lists resources of a specific type. | kubectl get pods |
| kubectl get -o wide | Provides a detailed list with extra information. | kubectl get services -o wide |
| kubectl get -o yaml | Retrieves a resource's definition in YAML format. | kubectl get deployment my-app -o yaml |
| kubectl describe | Shows detailed information about a single resource. | kubectl describe pod my-app-pod-12345 |

**Pod Interaction and Debugging**

| Command | Description | Example |
| --- | --- | --- |
| kubectl logs | Prints the logs for a container in a Pod. | kubectl logs my-pod |
| kubectl logs -f | Streams logs from a Pod (like tail -f). | kubectl logs -f my-pod |
| kubectl exec | Executes a command in a container. | kubectl exec -it my-pod -- /bin/sh |
| kubectl port-forward | Forwards a local port to a Pod's port. | kubectl port-forward my-pod 8080:80 |

**Deployments and Rollouts**

| Command | Description | Example |
| --- | --- | --- |
| kubectl scale | Scales a deployment to a new replica count. | kubectl scale deployment my-app --replicas=5 |
| kubectl rollout status | Watches the rollout of a deployment. | kubectl rollout status deployment my-app |
| kubectl rollout history | Displays the revision history of a deployment. | kubectl rollout history deployment my-app |
| kubectl rollout undo | Rolls back a deployment to a previous revision. | kubectl rollout undo deployment my-app |

**Namespaces**

| Command | Description | Example |
| --- | --- | --- |
| kubectl get ns | Lists all namespaces in the cluster. | kubectl get ns |
| kubectl create namespace | Creates a new namespace. | kubectl create namespace development |
| kubectl config set-context | Sets the current namespace for your context. | kubectl config set-context --current --namespace=development |

**Helper Commands**

| Command | Description | Example |
| --- | --- | --- |
| kubectl explain | Provides documentation for a resource. | kubectl explain pod |
| kubectl get all | Lists common resources (pods, services, deployments). | kubectl get all |

s