# Container Commands

This section covers essential commands to manage Docker containers effectively.

## Running a Container

Docker containers are lightweight, portable, and can be run with a simple command.

- Run a container with a specific image:
  ```bash
  docker container run <image name>
  docker container run nginx
  ```
This command pulls the `nginx` image from Docker Hub (if not already present) and starts a new container.
- Run a container in detached mode:
  ```bash
  docker container run -d nginx
  ```
The `-d` flag runs the container in the background, allowing you to continue using the terminal.

- Run a container with a specific name:
  ```bash
  docker run --name <container_name> <image_name>
  ```
  ```bash
  docker run --name anik ubuntu
  ```
  ```bash
  docker container run --name=<container_name> <image_name>
  docker container run --name=anik ubuntu
  ```
<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/specific-name.png" border="0">

- Run an interactive container
  ```bash
  docker run -it <image_name>
  ```
  ```bash
  docker run -it ubuntu
  ```

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/interactive.png" border="0">
  <br>
  
## Listing Containers
You can view information about running and stopped containers.
- List all running containers:
  ```bash
  docker container ls
  ```
- List all containers, including stopped ones:
  ```bash
  docker container ls -a
  ```
  <img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/All-Container.png" border="0">
  <br>

## Inspect & Execut a Containers
You can view Inspect & Execut a Containers.
- Inspect a container:
  ```bash
  docker inspect <container_id>
  ```
- Execute a command in a running container:
  ```bash
  docker exec <container_id> <command>
  ```
  ```bash
  docker exec fc2e537d9634 ls
  ```
  <img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/execute.png" border="0">
  <br>