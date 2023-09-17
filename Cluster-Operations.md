# Kind Kubernetes Cluster Operations
This file will contain all the information related to creating and working with the Kubernetes cluster with the Kind tool.

## Create Cluster
-  Create a single-node cluster
  ```
kind create cluster
```
- Create a single-node cluster with a specific name with the help of **--name** flag
```
kind create cluster --name=test-cluster
```
-  Create Multi-Node cluster with Configuration file
```
apiVersion: kind.x-k8s.io/v1alpha4
kind: Cluster
nodes:
  - role: control-plane
  - role: worker
  - role: worker
```
```
kind create cluster --config kind-config.yaml --name kind-multi-node
```
This will create a **kind-multi-node** Kubernetes cluster with one control plane and two worker nodes.
- Create a cluster with the following configuration file if ingress is being used.
```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  kubeadmConfigPatches:
  - |
    kind: InitConfiguration
    nodeRegistration:
      kubeletExtraArgs:
        node-labels: "ingress-ready=true"
  extraPortMappings:
  - containerPort: 80
    hostPort: 80
    protocol: TCP
  - containerPort: 443
    hostPort: 443
    protocol: TCP
```
```
kind create cluster --config=cluster-for-ingress.yaml --name ingress-cluster
```

## Access Cluster
- Get all the kind clusters
```
kind get clusters
```
- Get the cluster details
```
kubectl cluster-info --context <context-name>
```
- Access the cluster nodes
```
kubectl get nodes
```

