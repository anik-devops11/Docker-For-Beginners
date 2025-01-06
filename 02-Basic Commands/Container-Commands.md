# Container Commands 📄

This section covers essential commands to manage Docker containers effectively.

## Running a Container 🏃

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

- Run an interactive container:

  ```bash
  docker run -it <image_name>
  ```
  ```bash
  docker run -it ubuntu
  ```

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/interactive.png" border="0">
  <br>
  
## Listing Containers 📝
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

## Debugging Containers 🛠️
Docker provides tools to inspect and interact with containers.
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

- Attach to a running container:
  ```bash
  docker attach <container_id>
  ```
  ```bash
  docker attach bf4169807009
  ```
<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/attach.png" border="0">

- View logs for a running container:
  ```
  docker logs <container_id>
  ```
- View logs for a running container with timestamps:
  ```
  docker logs -t <container_id>
  ```
- View logs for a running container in real-time:
  ```
  docker logs -f <container_id>
  ```
- View logs for a running container in real-time with timestamps:
  ```
  docker logs -f -t <container_id>
  ```

Attach to a running container to view its real-time logs or output. This displays the live logs or output of the running `nginx` container.
Press `Ctrl+c` or press `Ctrl+d` for exit.

## Managing Container Lifecycle 🔗
Managing the lifecycle of a container is straightforward with Docker.

- Stop a running container:
    ```bash
    docker container stop <container_id>
    ```
- Start a stopped container:
    ```bash
    docker container start <container_id>
    ```
- Remove a container:
    ```bash
    docker container rm <container_id>
    ```
- Force remove a container (even if running):
    ```bash
    docker container rm -f <container_id>
    ```
- Restart a running container:
    ```bash
    docker container restart <container_id>
    ```
- Pause a running container:
    ```bash
    docker container pause <container_id>
    ```
<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/pause.png" border="0">

- Unpause a paused container:
    ```bash
    docker container unpause <container_id>
    ```
