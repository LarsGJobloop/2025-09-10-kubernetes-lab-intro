# 03 - Multiple Services

This example shows how to run multiple applications in the same cluster.

## What you'll learn
- Running multiple applications simultaneously
- How services isolate different applications
- Managing multiple deployments

## What's included
- `podinfo-deployment.yaml` & `podinfo-service.yaml` - The podinfo application
- `nginx-deployment.yaml` & `nginx-service.yaml` - A simple nginx web server

## How to run

1. **Start a local cluster:**
   ```bash
   kind create cluster --name k8s-lab
   ```

2. **Deploy all applications:**
   ```bash
   kubectl apply -f .
   ```

3. **Check what's running:**
   ```bash
   kubectl get pods
   kubectl get services
   kubectl get deployments
   ```

4. **Test both services:**
   ```bash
   # Test podinfo service
   kubectl run test-pod --image=busybox --rm -it --restart=Never -- wget -qO- http://podinfo-service

   # Test nginx service
   kubectl run test-pod --image=busybox --rm -it --restart=Never -- wget -qO- http://nginx-service
   ```

5. **Access from your local machine:**
   ```bash
   # Access podinfo
   kubectl port-forward service/podinfo-service 8080:80
   # Then visit http://localhost:8080

   # Access nginx (in another terminal)
   kubectl port-forward service/nginx-service 8081:80
   # Then visit http://localhost:8081
   ```

6. **Clean up:**
   ```bash
   kubectl delete -f .
   kind delete cluster --name k8s-lab
   ```

## What to explore
- Try scaling one application independently: `kubectl scale deployment podinfo --replicas=3`
- Use `k9s` to explore both applications
- Try deleting one service and see what happens to the other

## Learn More
- [Managing Multiple Applications](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#scaling-a-deployment)
- [Service Discovery](https://kubernetes.io/docs/concepts/services-networking/service/#discovering-services)
- [k9s Views](https://k9scli.io/topics/views/) - Interactive cluster exploration
