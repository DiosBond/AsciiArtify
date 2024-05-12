# Overview
*We will look at several tools that can be used to replace a full-fledged Kubernetes cluster. Their choice depends on the architecture and features of the implemented project, as well as the budget. I suggest you familiarize yourself with the comparative table and demo.*

## Compare table

|       | minikube  | kind  | k3d |
|---    |   :---------: |   :---------: |  :---------: |
| supported architectures	|   AMD64   |   AMD64	|   AMD64, ARMv7, ARM64
| supported container runtimes	| Docker,CRI-O,containerd,gvisor    | Docker    | Docker, containerd
| startup time | long |    middle	|   fast    |
| memory requirements |	2GB |	8GB |   512 MB  |
| cloud support |  + | not all function   | not all function  |
| complexity of usage | complex | easy |    easy    |
| multi-node support |	- | + |  + |

## Check your system for support virtualization
For Linux
```
grep -E --color 'vmx|svm' /proc/cpuinfo
```
For Windows
```
systeminfo
```

### **Minikube** 
Easy to install on GitHub codespases for local testing.
Support different hypervisors, as VirtualBox, KVM & Docker.

```
minikube start
```
#### Demo
![](../.data/demo_minikube.gif)

### **kind (Kubernetes IN Docker)**
Easy to install with go

```
go install sigs.k8s.io/kind@v0.22.0
kind create cluster
```

### **k3d**
Easy to install with curl

```
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
k3d cluster create three-node-cluster --agents 3
```