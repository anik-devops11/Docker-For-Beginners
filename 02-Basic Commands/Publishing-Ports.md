# Docker Port Mapping

This document explains Docker's port mapping functionality, including how to expose and access applications running inside Docker containers.

---

## What is Port Mapping?

Port mapping in Docker allows you to map a port from your host machine to a port inside a Docker container. This enables applications inside the container to be accessed externally.

---

## Why Use Port Mapping?

- **Access Applications**: Access containerized applications from your host or other devices.
- **Avoid Port Conflicts**: Map container ports to available host ports to avoid conflicts.
- **Run Multiple Containers**: Use different host ports to run multiple containers with the same internal ports.

---
## How to know port number?
### 1. Using docker `ls`

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/port_mapping1.png" border="0">
  - Look for the `PORTS` column in the output.
    - Note the PORTS column: `8080/tcp, 50000/tcp`
    - The host port is `8080.`
    - The container port is `50000.`

### 2. Using docker inspect
```
docker inspect <container_id>
```
  - In the output, look for the `Ports` section within the `NetworkSettings` field.
<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/port_mapping2.png" border="0">
## How to Map Ports in Docker

### Basic Syntax
```bash
docker run -p <host_port>:<container_port> <image_name>
```
`host_port`: The port on your host machine.

`container_port`: The port inside the container.

`image_name`: The Docker image to run.

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/port_mapping3.png" border="0">
`host_port`:  Host port is `9090`.

`container_port`: Container port is `8080`.

`image_name`: Image name is `jenkins/jenkins`.

### Now open your browser and navigating to

```
http://localhost:9090
```
```
http://<host_machine_ip>:8080
```

## Additional Information

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/port_mapping4.png" border="0">

In the image, we see the following in the `PORTS` column:

`0.0.0.0:9090->8080/tcp`

`Host Port:` `9090`

`Container Port:` `8080`

Meaning: Traffic coming to port `9090` on your host machine will be forwarded to port `8080` inside the Docker container.