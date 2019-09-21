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