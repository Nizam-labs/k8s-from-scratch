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
 1. Download and run the installer for the latest release.
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

