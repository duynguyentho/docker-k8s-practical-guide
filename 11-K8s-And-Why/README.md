# Kubernetes: Problems It Solves

## What is Kubernetes?
Kubernetes (K8s) is an open-source container orchestration platform that:
- Automates container deployment, scaling, and management
- Provides a declarative way to define cluster state
- Ensures high availability and reliability
- Manages containerized workloads and services

Key characteristics:
- **Production-grade**: Used by large enterprises worldwide
- **Portable**: Runs on public cloud, private cloud, or hybrid
- **Extensible**: Large ecosystem of tools and plugins
- **Self-healing**: Automatically replaces and reschedules failed containers
- **Service discovery**: Containers can find each other automatically
- **Load balancing**: Distributes network traffic for optimal performance

Originally developed by Google, now maintained by the Cloud Native Computing Foundation (CNCF).

## Common Container Deployment Challenges

### 1. Container Health Management
- Containers can crash or become unresponsive
- Manual monitoring is impractical
- Need automatic container replacement
- 24/7 availability requirements

### 2. Scaling Issues
- Traffic spikes require more container instances
- Workload distribution needs
- Manual scaling is inefficient
- Resource utilization optimization

### 3. Load Balancing
- Even traffic distribution across containers
- Multiple instances of same container
- Efficient request handling
- Prevent container overload

### 4. Manual Deployment Problems
- Security concerns with manual EC2/VM management
- OS and software updates
- Configuration management
- Resource allocation

## Why Kubernetes?
Kubernetes provides an automated solution for:
- Container orchestration
- Auto-scaling
- Load balancing
- Self-healing (automatic container replacement)
- Declarative configuration
- Zero-downtime deployments

## Key Benefits
- **Automation**: Reduces manual intervention
- **Reliability**: Ensures high availability
- **Scalability**: Handles varying workloads
- **Efficiency**: Optimizes resource usage
- **Consistency**: Maintains desired state

## Kubernetes Architecture

### Control Plane (Master Node)
- **API Server**: Central management point for the cluster
- **Scheduler**: Assigns pods to nodes
- **Controller Manager**: Maintains cluster state
- **etcd**: Distributed key-value store for cluster data

### Worker Nodes
- **Kubelet**: Manages containers on the node
- **Kube Proxy**: Handles network routing
- **Container Runtime**: Runs containers (Docker, containerd)
![alt text](image.png)
## Core Concepts

### 1. Pods
- Smallest deployable unit
- Contains one or more containers
- Shares network namespace
- Example:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-app
spec:
  containers:
  - name: app
    image: my-app:1.0
```

### 2. Deployments
- Manages Pod replicas
- Handles rolling updates
- Ensures desired state
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: app
        image: my-app:1.0
```

### 3. Services
- Provides stable network endpoint
- Load balances between pods
- Types: ClusterIP, NodePort, LoadBalancer
```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-app
spec:
  type: LoadBalancer
  ports:
  - port: 80
  selector:
    app: my-app
```

### 4. ConfigMaps & Secrets
- Store configuration data
- Separate config from code
- Secrets for sensitive data
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_URL: "http://api.example.com"
```

### 5. Volumes
- Persistent storage for pods
- Various storage backends
- Data survives pod restarts
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: app-data
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

## More Detail 
See 
<!-- # add Cheat-Sheet-Kube.pdf -->
[CheatSheet](Cheat-Sheet-Kubernetes.pdf) 
[Course resource](slides-kubernetes-intro.pdf) 