# K8S

To create a cluster with kubernetes and Ubuntu:

## Installation on all nodes

```
sudo apt-get update && sudo apt-get install -y apt-transport-https curl 

# Add the Docker Repository
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - 
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs)  stable" 

# Add the Kubernetes repository
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add - 
cat << EOF | sudo tee /etc/apt/sources.list.d/kubernetes.list 
deb https://apt.kubernetes.io/ kubernetes-xenial main 
EOF 

# Install Docker, Kubeadm, Kubelet, and Kubectl 
sudo apt-get update 
sudo apt-get install -y docker-ce kubelet=1.19.5-00 kubectl=1.19.5-00 kubeadm=1.19.5-00 

# Enable net.bridge.bridge-nf-call-iptables
echo "net.bridge.bridge-nf-call-iptables=1" | sudo tee -a /etc/sysctl.conf 
sudo sysctl -p 
```

## Installation on master node

```
# Initialize the cluster and configure kubectl
sudo kubeadm init

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

# Install the calico networking plugin
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml

# (Optional) If you want to be able to schedule Pods on the control-plane node
kubectl taint nodes --all node-role.kubernetes.io/master-
```

## Installation on worker node
The “kubeadm init …” will show you a “kubeadm join …” command at the end of the installation, which can be used to join the node to the Kubernetes cluster. The command will be something like the following:

```
sudo kubeadm join $controller_private_ip:6443 --token $token --discovery-token-ca-cert-hash $hash   
```

## Conclusion
Kubernetes cluster setup is done. To test the cluster working properly, we can run the following commands:

```
kubectl get nodes
```

