# 📦 Introduction to Containers

## 💡 What is a Container?

- A lightweight, portable unit of software.
- Includes everything needed to run an app.
- Runs consistently across environments.
- Multiple containers can run on one host (independent or working together).

## ⚔️ Containers vs Virtual Machines

| Feature    | Virtual Machine         | Container               |
| ---------- | ----------------------- | ----------------------- |
| OS         | Each VM has its own OS  | Shares host OS          |
| Size       | Heavy (GBs)             | Lightweight (MBs)       |
| Speed      | Slower to start         | Starts instantly        |
| Isolation  | Strong (via hypervisor) | Process-level isolation |
| Efficiency | Lower (redundant OSes)  | Higher (shared kernel)  |

## 🐳 Docker

- Lightweight containerization platform.
- Creates and manages containers.
- Easy to integrate with other tools.

### Docker Containers

- Portable → runs anywhere the Docker engine runs
- Single, immutable artifacts → ensure consistency between environments
- Efficient

### Docker Images

- Templates for containers
- Built on top of other images
- Self-written or pulled from a registry

> 🧩 **Example**

```
Image that uses Ubuntu as the base image. Then, it has our libraries, a web server, and the application.
```

### Dockerfile

- Instructions for building a Docker image
- Each instruction is a layer in the image

> 🧩 **Example**

```dockerfile
FROM ubuntu:latest
CMD echo "Hello World"
```

## 🔬 Microservices

Containers are the foundation that make microservices architecture practical.

- Designed to speed up development and deployment.
- Improves scalability and maintainability.
- Each service fulfills a single purpose.
- Decentralized architecture.
- Smart endpoints, dumb pipes.
- Designed for failure.
- Disposable.
