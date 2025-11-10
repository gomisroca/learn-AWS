# 🗃️ Amazon EKS Primer

- EKS is a managed k8s service that facilitates deploying, managing and scaling k8s clusters on AWS.
- EKS facilitates automating tasks such as patching, node provisioning, and updating.
- EKS manages aspects such as scheduling containers, monitoring, scaling and integrating with other AWS services.

## 🛞 Kubernetes Review

**k8s Objects**:

- Cluster: Set of worker machines (nodes) that run containers.
- Node: Virtual or physical machine that contains the necessary services to run pods.
- Pod: A group of one or more containers.
- Ephemeral Volume: Apps in a pod share a volume. When the pod is deleted, the volume is also deleted.
- Persistent Volume: Apps in a pod share a volume. Lifecycle of the volume is independent of the pod.
- Service: A group of pods and a means to access them.
- Namespace: Virtual cluster backed by the same physical cluster.
- ReplicaSet: Ensures a specific number of pod replicas are running at any given time.
- Deployment: Owns and manages ReplicaSets or pods. Changes the state of the cluster to the desired state.
- ConfigMap: API object that stores non-secret configuration data.
- Secret: API object that stores sensitive data.

**Pod Scheduling** can be done via the k8s scheduler. It will check the resources required and use that information to decide which node to run the pod on. It will then filter ineligible nodes and run the pod on the eligible nodes.

**Control Plane** nodes manage the worker nodes and the pods in the cluster.  
**Data Plane** worker nodes host the pods that are the components of the application.

We can extend the k8s API with **Custom Resources** to add additional functionality to the cluster. They are created with a Custom Resource Definition (CRD). They can be controlled with custom controllers, which run in pods on the worker nodes. When used to automate the management of custom resources, they are called **Operators**.

We can communicate with the control plane using the **kubectl** cli.

## 🎮 EKS Control Plane

- EKS manages the k8s control plane.
- In standard k8s we are responsible for designing, implementing and maintaining all components of the control plane.
- EKS automatically manages the availability and scalability of the k8s API servers and etcd persistence layer for each cluster.

Getting Started with EKS:

- EKS control panel consists of 2 API servers nodes and 3 etcd nodes across 3 availability zones.
- EKS auto detects and replaces unhealthy control plane nodes.
- First, we provision the cluster of worker nodes. Then, EKS will provision the control plane nodes.
- We connect to the control plane nodes using cli or gui. Then, we can deploy applications to the cluster just like in any other k8s cluster.
- EKS has 2 CLIs: Amazon EKS CLI and eksctl.

What API are we using?

- We use EKS API for anything EKS manages. i.e Control panel (creating and managing cluster)
- We use k8s API for k8s objects such as pods, deployments, services, etc.

## 📊 EKS Data Plane

- EKS can manage some of all of the data plane.
- There's three degrees of control over the data plane:
  - Self-managed: EKS only manages the control plane.
  - Managed Node Groups: EKS manages the node groups and EC2 instances within them.
  - AWS Fargate: EKS fully manages the data plane.

# ⚙️ Configuring AWS EKS

## 🍳 Preparing the AWS Environment

- When creating an EKS cluster we need to perform 3 tasks:
  - Secure the AWS environment
  - Configure the virtual private cloud (VPC) for the cluster
  - Create the EKS cluster
- AWS handles EKS control plane:
  - K8s control-plane nodes and services
  - etcd
- We as users handle EKS data plane:
  - IAM
  - Image, Pod, Runtime and Network Security
- Three permission types:
  - Cluster IAM Role: Allows EKS to make calls to AWS APIs for the cluster on our behalf.
  - Node IAM Role: Allows EKS to make calls to AWS APIs for the node on our behalf.
  - RBAC User: Admin user for the cluster.
- Three networking configurations:
  - Only Public Subnets: All workers have a public IP address and can send/receive traffic via a gateway.
  - Only Private Subnets: Nodes may send/receive traffic only via a NAT gateway.
  - Public and Private Subnets: Nodes may send/receive traffic via NAT or to the internet.

## 🎨 Creating a Cluster

- AWS CLI, kubectl, eksctl required.

Using **eksctl**:

- `eksctl create cluster -f ./config.yaml` to create the cluster.
- We can add arguments to the command or create a config file:

```yaml
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig
metadata:
  name: eks-cluster
  region: us-west-2
vpc:
  subnets:
    private:
      us-east-1b: { id: subnet-0a1d2c3d }
      us-east-1c: { id: subnet-0a1d2c3d }
nodeGroups:
  - name: ClusterTwoNodes
    instanceType: t3.medium
    desiredCapacity: 2
    privateNetworking: true
```

## 🌅 Configuring Horizontal and Vertical Scaling

- Horizontal Scaling: increase/decrease performance by adding/removing compute resources (such as pods).
- Vertical Scaling: increase performance by adding more resources, such as CPU, memory, or storage.
- The k8s Cluster Autoscaler automatically scales the number of nodes in the cluster. Karpenter is an alternative to the Cluster Autoscaler.
- There is Horizontal Autoscaler and Vertical Autoscaler.
