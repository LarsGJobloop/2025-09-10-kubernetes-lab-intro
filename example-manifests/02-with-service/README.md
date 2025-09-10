# 02 - Deployment with Service

This example adds a Service to make your application accessible within the cluster.

## What you'll learn
- How Services provide stable network access to pods
- The difference between ClusterIP and other service types
- How pods can communicate with each other

## What's included
- `deployment.yaml` - Same podinfo application
- `service.yaml` - Service that exposes the podinfo application

## How to run

1. **Start a local cluster:**
   ```bash
   kind create cluster --name k8s-lab
   ```

2. **Deploy both the application and service:**
   ```bash
   kubectl apply -f .
   ```

3. **Check what's running:**
   ```bash
   kubectl get pods
   kubectl get services
   kubectl get deployments
   ```

4. **Test the service:**
   ```bash
   # Create a temporary pod to test connectivity
   kubectl run test-pod --image=busybox --rm -it --restart=Never -- wget -qO- http://podinfo-service
   ```

5. **Clean up:**
   ```bash
   kubectl delete -f .
   kind delete cluster --name k8s-lab
   ```

## What to explore
- Try accessing the service from different pods
- Use `kubectl port-forward service/podinfo-service 8080:80` to access from your local machine
- Explore the service endpoints with `kubectl get endpoints`

## Learn More
- [Kubernetes Services](https://kubernetes.io/docs/concepts/services-networking/service/)
- [Service Types](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types)
- [Port Forwarding](https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/)
