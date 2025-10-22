# minikube start

minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away: `minikube start`

## What you’ll need

* 2 CPUs or more
* 2GB of free memory
* 20GB of free disk space
* Internet connection
* Container or virtual machine manager, such as: Docker, QEMU, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMware Fusion/Workstation

## 1 Installation
Click on the buttons that describe your target platform. For other architectures, see the release page for a complete list of minikube binaries.

### Operating system
* Windows
### Architecture
* x86-64
### Release type
* Stable

### Installer type
* .exe download
  

To install the latest minikube `stable` release on `x86-64` Windows using .exe download:
```
 1. Download and run the installer for the latest release(https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe).
Or if using PowerShell, use this command:

New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
$ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri 'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing

2. Add the minikube.exe binary to your PATH.
Make sure to run PowerShell as Administrator.

$oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
if ($oldPath.Split(';') -inotcontains 'C:\minikube'){
  [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine)
}

If you used a terminal (like powershell) for the installation, please close the terminal and reopen it before running minikube.
```


## 2 Start your cluster

From a terminal with administrator access (but not logged in as root), run:

```shell
minikube start

```

If minikube fails to start, see the  [drivers page](https://minikube.sigs.k8s.io/docs/drivers/)  for help setting up a compatible container or virtual-machine manager.

## 3 Interact with your cluster

If you already have kubectl installed (see  [documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/)), you can now use it to access your shiny new cluster:

```shell
kubectl get po -A

```

Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

```shell
minikube kubectl -- get po -A

```

You can also make your life easier by adding the following to your shell config: (for more details see:  [kubectl](https://minikube.sigs.k8s.io/docs/handbook/kubectl/))

```shell
alias kubectl="minikube kubectl --"

```

Initially, some services such as the storage-provisioner, may not yet be in a Running state. This is a normal condition during cluster bring-up, and will resolve itself momentarily. For additional insight into your cluster state, minikube bundles the Kubernetes Dashboard, allowing you to get easily acclimated to your new environment:

```shell
minikube dashboard
```
## 4 Deploy applications

-   [Service](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download#Service)
-   [LoadBalancer](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download#LoadBalancer)
-   [Ingress](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download#Ingress)

Create a sample deployment and expose it on port 8080:

```shell
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube --type=NodePort --port=8080

```

It may take a moment, but your deployment will soon show up when you run:

```shell
kubectl get services hello-minikube

```

The easiest way to access this service is to let minikube launch a web browser for you:

```shell
minikube service hello-minikube

```

Alternatively, use kubectl to forward the port:

```shell
kubectl port-forward service/hello-minikube 7080:8080

```

Tada! Your application is now available at  [http://localhost:7080/](http://localhost:7080/).

You should be able to see the request metadata in the application output. Try changing the path of the request and observe the changes. Similarly, you can do a POST request and observe the body show up in the output.

## 5 Manage your cluster

Pause Kubernetes without impacting deployed applications:

```shell
minikube pause

```

Unpause a paused instance:

```shell
minikube unpause

```

Halt the cluster:

```shell
minikube stop

```

Change the default memory limit (requires a restart):

```shell
minikube config set memory 9001

```

Browse the catalog of easily installed Kubernetes services:

```shell
minikube addons list

```

Create a second cluster running an older Kubernetes release:

```shell
minikube start -p aged --kubernetes-version=v1.34.0

```

Delete all of the minikube clusters:

```shell
minikube delete --all
```
