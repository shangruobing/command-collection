# kubernetes

## Install

```shell
# Install kubectl on macOS
brew install kubectl
# Test to ensure the version
kubectl version
```

## Minikube

Minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernete. Minikube is a lightweight Kubernetes implementation that creates a VM on your local machine and deploys a simple cluster containing only one node.

```shell
brew install minikube
# start your cluster
minikube start
# stop your cluster
minikube stop
# dashboard
minikube dashboard
```

### Create a Deployment

A Kubernetes Pod is a group of one or more Containers, tied together for the purposes of administration and networking. A Kubernetes Deployment checks on the health of your Pod and restarts the Pod's Container if it terminates. Deployments are the recommended way to manage the creation and scaling of Pods.

```shell
# Run a test container image that includes a webserver
kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080
# View the Deployment
kubectl get deployments
# View the Pod
kubectl get pods
# View cluster Events
kubectl get events
# View the kubectl configuration
kubectl config view
# View application logs for a container in a pod.
kubectl logs container_name
```

### Create a Service

By default, the Pod is only accessible by its internal IP address within the Kubernetes cluster. To make the Container accessible from outside the Kubernetes virtual network, you have to expose the Pod as a Kubernetes Service.

```shell
# Expose the Pod to the public internet
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
# View the Service you created
kubectl get services
# On cloud providers that support load balancers, an external IP address would be provisioned to access the Service. On minikube, the LoadBalancer type makes the Service accessible through the minikube service command.
minikube service hello-node
```

### Enable addons

The minikube tool includes a set of built-in addons that can be enabled, disabled and opened in the local Kubernetes environment.

```shell
# List the currently supported addons
minikube addons list
# Enable an addon
minikube addons enable metrics-server
# View the Pod and Service you created by installing that addon
kubectl get pod,svc -n kube-system
# Check the output from metrics-server
kubectl top pods
# Disable metrics-server
minikube addons disable metrics-server
```

### Clean up

```shell
# Clean up the resources you created in your cluster
kubectl delete service hello-node
kubectl delete deployment hello-node
# Stop the Minikube cluster
minikube stop
# Optionally, delete the Minikube VM:
minikube delete
```

## Common

```shell
# list resources
kubectl get -
# show detailed information about a resource
kubectl describe -
# print the logs from a container in a pod
kubectl logs -
# execute a command on a container in a pod
kubectl exec -
# View the Node
kubectl get nodes
# View the Deployment
kubectl get deployments
# View the Pod
kubectl get pods
# View cluster Events
kubectl get events
# View the kubectl configuration
kubectl config view
# View application logs for a container in a pod.
kubectl logs container_name
```

