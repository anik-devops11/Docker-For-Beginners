# What is Docker?

Docker is a platform designed to simplify the creation, deployment, and management of containers. It allows developers to package applications and their dependencies into containers that are portable and consistent.

## Key Components of Docker:
- **Docker Client**: Interface to communicate with the Docker Daemon.
- **Docker Daemon**: Manages containers, images, and networks.
- **Docker Hub**: Central registry for sharing container images.

### Advantages of Docker:
1. Portability: Containers run seamlessly across different environments.
2. Resource Efficiency: Shares the OS kernel for reduced overhead.
3. Simplified DevOps: Ensures consistency between development and production.

```bash
# Example: Running an NGINX container
$ docker run nginx