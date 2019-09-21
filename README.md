# Kubernetes Cluster Bootstrapping
## Summary
This is a simple bash script to bootstrap a Kubernetes cluster, control plane and nodes using `kubeadm`.

## Requirements
- You need SSH and root access in the machines where you're running these scripts on.
- The scripts will work on Ubuntu 16.04+.

## Steps:
### 1. Installing required binaries
Run `install-requirement` script on all your machines (nodes).<br>
The script requires a Kubernetes version to install the corresponding binaries for that specific version.<br>
Example: `./install-requirements 1.14.7` <br>
Find latest Kubernetes releases from: 
https://github.com/kubernetes/kubernetes/releases

### 2. Initialising the control plane
Run `init-master` script to initialise your control plane.<br>
The default network provider set in the script is `Calico` and the default Pod CIDR is set to: `10.10.0.0/16`. Feel free to change these as desired.<br>
Take a note of the join command that's printed at the end when you run this script. <br>
It'll be something like:<br> `kubeadm join <Master node's IP Address>:6443 --token 8tipwo.tst0nvf7wcaqjcj0 \
      --discovery-token-ca-cert-hash \
      sha256:f2a5b22b658683c3634459c8e7617c9d6c080c72dd149f3eb903445efe9d8346`

### 3. Join worker nodes
Run the join command from the previous step on all of your worker nodes.<br>
When you login to your master node (or if you have copied the kubeconfig to your local machine), you should be able to see all your nodes with a "Ready" state when you run: `kubectl get nodes`