# Available Tools Reference

This document provides quick reference for the Kubernetes tools available in this environment.

## kind - Kubernetes in Docker

Creates lightweight Kubernetes clusters using Docker containers.

### Common Commands
```bash
# Create a new cluster
kind create cluster --name k8s-lab

# List existing clusters
kind get clusters

# Delete a cluster
kind delete cluster --name k8s-lab

# Load a local Docker image into the cluster
kind load docker-image my-app:latest --name k8s-lab
```

### Why kind?
- **Fast**: Clusters start in seconds
- **Lightweight**: Uses Docker containers instead of VMs
- **Isolated**: Won't affect your system
- **Perfect for learning**: Easy to create/destroy clusters

## kubectl - Kubernetes Command Line

The main tool for interacting with Kubernetes clusters.

### Essential Commands
```bash
# Cluster information
kubectl cluster-info
kubectl get nodes

# Working with resources
kubectl get pods
kubectl get services
kubectl get deployments

# Apply configurations
kubectl apply -f deployment.yaml
kubectl apply -f .

# Delete resources
kubectl delete -f deployment.yaml
kubectl delete pod my-pod

# Get detailed information
kubectl describe pod my-pod
kubectl describe service my-service

# View logs
kubectl logs my-pod
kubectl logs -f my-pod  # Follow logs

# Execute commands in pods
kubectl exec -it my-pod -- /bin/sh

# Port forwarding (access services locally)
kubectl port-forward service/my-service 8080:80
```

### Useful Flags
- `-o wide` - Show more details
- `-o yaml` - Show YAML output
- `--watch` - Watch for changes
- `-n namespace` - Work in specific namespace

## k9s - Terminal UI

Interactive terminal interface for Kubernetes.

### Getting Started
```bash
# Start k9s
k9s

# Navigate with arrow keys
# Press '?' for help
# Press 'q' to quit
```

### Key Shortcuts
- `d` - Describe selected resource
- `l` - View logs
- `s` - Shell into pod
- `e` - Edit resource
- `d` - Delete resource
- `:` - Command mode
- `?` - Help

### Views Available
- **Pods** - See all running pods
- **Services** - View services and their endpoints
- **Deployments** - Manage deployments
- **Nodes** - Cluster node information

## Quick Troubleshooting

### Common Issues

**"cluster not found"**
```bash
# Check if cluster exists
kind get clusters

# Create if missing
kind create cluster --name k8s-lab
```

**"connection refused"**
```bash
# Check cluster status
kubectl cluster-info

# Restart cluster if needed
kind delete cluster --name k8s-lab
kind create cluster --name k8s-lab
```

**"image pull failed"**
```bash
# For local images, load them into kind
kind load docker-image my-image:latest --name k8s-lab
```

### Getting Help
- `kubectl --help` - General help
- `kubectl get --help` - Help for specific commands
- `k9s` then press `?` - Interactive help in k9s

### CLI Reference Links
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) - Quick command reference
- [kubectl Commands](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) - Complete command list
- [kind CLI Reference](https://kind.sigs.k8s.io/docs/user/quick-start/) - kind command reference
- [k9s Key Bindings](https://k9scli.io/topics/keybindings/) - k9s keyboard shortcuts

## Pro Tips

- **All tools are preconfigured**: Aliases, completions, and essential utilities like `kubectl` and `k9s` are already set up in your Dev Container environment. No extra setup is needed.

- **Explore with k9s**: Use `k9s` for an interactive view of your cluster. Just run `k9s` in the terminal.

- **Check resource status**: Always verify your deployments are running as expected:
  ```bash
  kubectl get pods -o wide
  kubectl describe deployment <your-deployment-name>
  ```

- **Use the provided environment**: The Dev Container with NixOS and `flake.nix` ensures a consistent, ready-to-use Kubernetes tooling setup for all users.
