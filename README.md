On Master: 

Initialize the cluster (Execute the following command only on the Master node):

sudo kubeadm init --pod-network-cidr=10.244.0.0/16

Set up local kubeconfig(Execute the following command only on the Master node):

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config


Apply Flannel CNI network overlay(Execute the following command only on the Master node):

sudo kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml



On Node1 and Node 2: 

Join the worker nodes to the cluster (Execute the following command only on Node1 and Node2):

sudo kubeadm join 172.31.4.161:6443 --token 0y52t6.ffsj8jkjfcl1sq8h \
   --discovery-token-ca-cert-hash sha256:7aa1825042d19d3e567f7e4b447634e942fe9ed7f18f78464a9c05f451551ed5



Verify the worker nodes have joined the cluster successfullyExecute the following command on the Master Node):

kubectl get nodes
# ubeadm-AWS-ubuntu_Instance-
