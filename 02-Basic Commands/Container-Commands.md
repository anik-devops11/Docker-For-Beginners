# Container Commands

This section covers essential commands to manage Docker containers effectively.

## Running a Container

Docker containers are lightweight, portable, and can be run with a simple command.

- Run a container with a specific image:
  ```bash
  docker container run nginx
  ```
This command pulls the `nginx` image from Docker Hub (if not already present) and starts a new container.
- Run a container in detached mode:
  ```bash
  docker container run -d nginx
  ```
The `-d` flag runs the container in the background, allowing you to continue using the terminal.
## Listing Containers
You can view information about running and stopped containers.
- List all running containers:
  ```bash
  docker container run -d nginx
  ```
- List all containers, including stopped ones:
  ```bash
  docker container ls -a
  ```