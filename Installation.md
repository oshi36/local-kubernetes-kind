# Setting up Kind tool 

## Prerequisites
- Install docker on the machine. Install according to your machine type. Here, I have taken Linux Ubuntu for installation. Run the following commands.
```
apt update && apt install docker.io -y
```
- Install kubectl CLI tool for accessing the clusters
``` 
    curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
    echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
    sudo apt-get update && sudo apt-get install -y kubectl
```
## Install Kind Binary Tool

- Install kind with the help of release binaries. Visit official docs [here](https://kind.sigs.k8s.io/docs/user/quick-start/) for other ways.
```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64
chmod +x ./kind
mv ./kind /usr/local/bin/kind
```
- Verify the kind version
```
kind version
```
