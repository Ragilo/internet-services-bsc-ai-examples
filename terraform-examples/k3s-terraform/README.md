# Minimalistic k3s deployment example for HS Fulda NetLab OpenStack

Start by cloning the repo.

```
git clone https://github.com/srieger1/internet-services-bsc-ai-examples.git
```

Go to the terraform/k3s-terraform folder and change the parameters in [main.tf](https://github.com/srieger1/internet-services-bsc-ai-examples/blob/main/terraform-examples/k3s-terraform/main.tf) to your username and password. Afterwards run:

```
terraform init
terraform apply
```

After terraform is finished you will get a floating IP of the k3s server. Login using the SSH key used for the deployment. kubectl is already installed. helm etc. needs to be installed. You can check:

```
kubectl --kubeconfig /etc/rancher/k3s/k3s.yml get nodes
kubectl --kubeconfig /etc/rancher/k3s/k3s.yml get pods -n kube-system
```

As this is a minimalistic approach, you need to install everything else yourself (kubernetes deployments, services, daemonsets, pods etc.). E.g., you can find a helm chart to deploy openstack-cloud-controller and other examples in https://github.com/srieger1/internet-services-bsc-ai-examples/tree/main/terraform-examples/k3s-terraform/manifests.

When you do not want to manage Kubernetes entirely on your own, you can use the RKE2 deployment provided at: https://github.com/srieger1/terraform-openstack-rke2. A deployment that requires even less manual intervention and provides the installation of a Kubernetes cluster using the Web UI of a rancher deployment host is provided here: https://github.com/srieger1/internet-services-bsc-ai-examples/tree/main/terraform-examples/rancher-terraform.
