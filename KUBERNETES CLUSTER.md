



**The Control Plane is responsible for managing the cluster.**

**The Control Plane is responsible for managing the cluster.**

**Node-level components, such as the kubelet, communicate with the control plane using the [Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/)**, which the control plane exposes.


COMPONENTS
- Pod
- Services - permanant IP and Load balancer
- Ingress
- Configmap
- Secrets
- Volumes
- Deployments - replica or blue prints
	-  DB cant be replicated via blueprint
- Stateful Set - for database replics
	- very tough
	- so better to host the database outside the environment and connect them to the pod


K8S Architecture

- KUBELET - interface with bot  container runtime and the machine itself
- KUBE PROXY - communication via services

MASTER SERVICES

- API Server - cluster gateway
	- request forwarding
	- single entry point
- Scheduler - start app in the worker node
	- where the pod will be scheduled
	- scheduler only decides the node where the app has to be started it is the function of kubelet
- Controller Manager - detect state changes
	- recover crash state
	- it request scheduler to reschedule the pods
- etcd - Key_Value store
	- every mechanism is stored here as data


MINIKUBE - both master and worker run in the same machine for testing purposes.


## Create a Service

By default, the Pod is only accessible by its internal IP address within the Kubernetes cluster. To make the `hello-node` Container accessible from outside the Kubernetes virtual network, you have to expose the Pod as a Kubernetes Service


pods
replica sets
deployments
services


1. Create a POD
```
kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080
```

4. View cluster events:
```
kubectl get events
```

5. View the `kubectl` configuration:
```
kubectl config view
```

Expose the Pod to the public internet using the `kubectl expose` command:

```
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```

The `--type=LoadBalancer` flag indicates that you want to expose your Service outside of the cluster.

# Crud Commands

```
Create  deployment kubectl create deployment [name]
```

```
Edit  deployment kubectl edit deployment [name]
```

```
Delete deployment  kubectl delete deployment [name]
```

# Status of different K8s components

```
kubectl get nodes 
```

```
kubectl get pod -o wide
 ```

```
kubectl get services
```

```
kubectl get replicaset
```

```
kubectl get deployment
```

# Debugging pods

1. Log to Console
```
kubectl logs [pod name]
```

2. Get Interactive Terminal
```
kubectl exec -it [pod name] --bin/bash
```

3. Get info about pod
```
kubectl describe pod [pod name]
```

4. Get info about service
```
kubectl describe service [service name]
```
# Use configuration file for CRUD

1. Apply a configuration file
```
kubectl apply -f [file name]
```

2. Delete with configuration file
```
kubectl delete -f [file name]
```

# 3 PARTS of K8s configuration file

1. Metadata 
2. Specification
3. Status - automatically generated

```
kubectl get deployment [deploymrnt name] -o yaml
```