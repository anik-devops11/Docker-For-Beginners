# Images Commands 🚀

This section covers essential commands to manage Docker images effectively.

## List and Inspect Images 🔎

- List all Docker images on your system:
  ```bash
  docker images
  ```
- Show detailed information about an image:
  ```bash
  docker inspect <image_name>
  ```
- List dangling images (untagged images):
  ```bash
  docker images -f "dangling=true"
  ```
## Pull and Push Images 📥

- Pull an image from a registry (e.g., Docker Hub):
  ```bash
  docker pull <image_name>
  ```
- Push an image to a registry:
  ```
  docker push IMAGE[:TAG]
  ```
#### Example:
  ```
  docker push username/repo:tag
  ```
## Remove Images 🗑️
- Remove a specific image:
  ```
  docker rmi <image_name>
  ```
- Remove all unused images:
  ```
  docker image prune
  ```
- Remove all unused images, containers, volumes, and networks:
  ```
  docker system prune
  ```
- Force clean up everything, including stopped containers:
  ```
  docker system prune -a
  ```
