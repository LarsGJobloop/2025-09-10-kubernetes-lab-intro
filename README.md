# Kubernetes Learning Lab

> [!NOTE]
> **Prerequisites**: This lab requires Docker (or compatible container runtime) and Git to be installed locally. Ask an instructor if in doubt. If you're setting up independently, see [Docker installation](https://docs.docker.com/get-docker/) and [Git installation](https://git-scm.com/downloads).

Welcome to your first Kubernetes learning environment! This repository provides a safe, isolated sandbox for exploring Kubernetes concepts step by step.

## 🎯 What This Lab Provides

This is a **beginner-friendly experimental sandbox** designed to help you:
- Get hands-on experience with Kubernetes
- Learn core concepts through progressive examples
- Experiment safely without affecting your system
- Build confidence before moving to more advanced labs

## 🛠️ Available Tools

This environment comes pre-configured with essential Kubernetes tools:

- **`kind`** - Creates lightweight Kubernetes clusters for testing
- **`kubectl`** - Command-line tool for managing Kubernetes clusters
- **`k9s`** - Interactive terminal UI for exploring your cluster

## 🚀 Getting Started

### 0. Enable Dockerd TCP communication over the local interface

1. Edit docker.json in:

- Windows Docker Desktop: `C:\ProgramData\docker\config\daemon.json`
- Linux, Docker Desktop: `/etc/docker/daemon.json`
- Linux Rootless, Docker Desktop: `~/.config/docker/daemon.json`
- MacOS OrbStack:`~/.orbstack/config/docker.json`

2. Restart the Docker Daemon

Configuration
```json
{
  "hosts": [
    "unix:///var/run/docker.sock",
    "tcp://127.0.0.1:2375"
  ]
}
```

### 1. Open in Dev Container
This project uses Dev Containers for consistent, isolated development environments:
1. Open in VS Code and choose "Reopen in Container" when prompted
    - Or use any compatible editor with Dev Container support
2. Load the development environment

    ```sh
    nix develop
    ```

#### If adding new CLI/Binaries

Reload the development environment

    ```sh
    exit
    nix develop
    ```

### 2. Start Your First Cluster
```bash
# Create a local Kubernetes cluster
kind create cluster --name k8s-lab

# Verify it's working
kubectl cluster-info
kubectl get nodes
```

### 3. Explore the Examples
Navigate to the `example-manifests/` directory and work through the examples in order:

1. **[01-basic-deployment](example-manifests/01-basic-deployment/)** - Your first Kubernetes deployment
2. **[02-with-service](example-manifests/02-with-service/)** - Adding network access with Services
3. **[03-multiple-services](example-manifests/03-multiple-services/)** - Running multiple applications

Each example includes:
- ✅ Ready-to-run Kubernetes manifests
- 📖 Step-by-step instructions
- 🔍 Things to explore and experiment with

## 📚 Learning Path

### Example 1: Basic Deployment
- Deploy your first application
- Understand pods and deployments
- Learn basic kubectl commands

### Example 2: Deployment with Service
- Add network access to your application
- Understand how Services work
- Learn about pod-to-pod communication

### Example 3: Multiple Services
- Run multiple applications simultaneously
- Understand service isolation
- Practice managing multiple deployments

## 🧪 Experimentation Tips

- **Don't worry about breaking things** - This is a sandbox environment
- **Try modifying the examples** - Change replica counts, ports, or configurations
- **Use `k9s`** - Press `?` to see all available commands
- **Explore with `kubectl`** - Try `kubectl get`, `kubectl describe`, `kubectl logs`

## 🧹 Cleanup

When you're done experimenting:
```bash
# Delete your cluster
kind delete cluster --name k8s-lab

# Or delete specific resources
kubectl delete -f example-manifests/01-basic-deployment/
```

## 🔄 Starting Fresh

To reset everything and start over:
```bash
# Delete existing cluster
kind delete cluster --name k8s-lab

# Create a new cluster
kind create cluster --name k8s-lab
```

## 📖 Additional Resources

### Official Kubernetes Documentation
- [Kubernetes Documentation](https://kubernetes.io/docs/) - Complete official docs
- [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) - Core concepts explained
- [Kubernetes Tutorials](https://kubernetes.io/docs/tutorials/) - Step-by-step tutorials
- [kubectl Reference](https://kubernetes.io/docs/reference/kubectl/) - Complete kubectl documentation
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) - Quick reference

### Tool Documentation
- [kind Documentation](https://kind.sigs.k8s.io/) - Creating clusters with kind
- [k9s Documentation](https://k9scli.io/) - Terminal UI for Kubernetes

### Learning Paths
- [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) - Official interactive tutorial
- [Kubernetes by Example](http://kubernetesbyexample.com/) - Practical examples
- [Play with Kubernetes](https://labs.play-with-k8s.com/) - Online playground

## 🎓 Next Steps

Once you're comfortable with these basics, you'll be ready for more advanced labs that cover:
- ConfigMaps and Secrets
- Ingress and external access
- Persistent storage
- And much more!

---

**Remember**: This is a learning environment. Experiment freely, break things, and learn from the experience!
