Tags: #microservicios #k8s

There are four core concepts that you must know to be able to understand K8s: 

- Node 
- Cluster
- Control Plane
- Data Plane

![[k8sArch.excalidraw]]

The ***Cluster*** is the set of resources that make the Kubernetes system and those are made of ***Nodes***, each node is a server that can be a virtual machine  or a bare metal system (like a real machine).

The nodes are going to be split up in two groups:
- Control Plane group (also knows as Control Plane Nodes): System componentes of Kubernetes
- Data plane group (also known as Worker Nodes): Where all our application will live

![[k8sArchFull.excalidraw]]

Control pane node agents
- c-c-m (Cloud Controller Manager): API communication between K8s and the cloud provider, for example, if you need a loud balancer. All the resources that needs to be provided outside of K8s to the cloud provider.
- c-m (Controller Manager): This controller is in-charge of making sure that all the other controllers are up and healthy.
- api: This is the the main line for all our operations, we use this to be able to do all the operations inside our k8s system.
- etcd: Datastore of k8s to manage all the resources, and is based on a key-value pair.
- sched: Assign pods to new nodes based on their current usage. Based on conditions of the physical devices, we can search for a new node for our pod.

Worker node agents
- kubelet: Component in-charge of spawn, manage and monitor the workloads. 
- k-proxy: Networking between the workloads.

> I will focus just in the Worker nodes, most of the cloud providers helps with the Control Pane

## Standard interfaces
This are the ones who run the runtime of the containers (execution, networking and storing), we can select which one we want to use.

- Container Runtime Interface (CRI)
	- Containerd 1.0
	- cri-o
- Container Network Interface (CNI)
	- Calico
	- Flannel
	- Cilium (no use of k-proxy)
	- Cloud Specific
		- Amazon VPC CNI
		- Azure CNI
		- Google Cloud CNI
- Container Storage Interface (CSI)
	- Cloud Specific CSI Driver
		- Amazon EBS CSI Driver
		- Compute Engine persistent disk (GCP)
		- Azure Disk Container CSI Driver
	- Cert manager CSI Driver
	- Secretes Store CSI Driver

> We can check the maturity of some of the cloud projects here [link](https://landscape.cncf.io/)

