# 01 - Basic Deployment

This example shows the simplest Kubernetes deployment - running a single application pod.

## What you'll learn
- How to deploy an application using Kubernetes
- Understanding pods and deployments
- Basic kubectl commands

## What's included
- `deployment.yaml` - Creates a pod running the podinfo application

## How to run

1. **Start a local cluster:**
   ```bash
   kind create cluster --name k8s-lab
   ```

2. **Deploy the application:**
   ```bash
   kubectl apply -f deployment.yaml
   ```

3. **Check if it's running:**
   ```bash
   kubectl get pods
   kubectl get deployments
   ```

4. **Clean up:**
   ```bash
   kubectl delete -f deployment.yaml
   kind delete cluster --name k8s-lab
   ```

## What to explore
- Try changing the number of replicas in the deployment
- Use `kubectl describe deployment podinfo` to see detailed information
- Use `k9s` to explore the cluster interactively

## Learn More
- [Kubernetes Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- [Kubernetes Pods](https://kubernetes.io/docs/concepts/workloads/pods/)
- [kubectl Commands](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
