# Images Commands 🚀

This section covers essential commands to manage Docker images effectively.
----
<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/Images Commands visual selection.png" border="0">

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
- forcefully remove a specific image using its name or image ID:
  ```
  docker image rm -f <image-name-or-id>
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
- Forcefully remove images:
  ```
  docker image rm -f <image-name-or-id>
  ```
- Forcefully remove all images:
  ```
  docker image rm -f $(docker images -aq)
  ```
----
## Additional Tips 💡

- If you want to give the image name and tag, you can use the `docker tag` command:

  ```
  docker tag <image_id> <give_image_name>
  ```
  Example:
  ```
  docker tag 72f6e2460071 my_image:v1
  ```
- Save image as a file

  ```
  docker image save <image_name> -o <file_name>.tar
  ```
  Example:
  ```
  docker image save nginx -o my_image.tar
  ```

- Load image from a file:

  ```
  docker image load -i <file_name>.tar
  ```
  Example:
  ```
  docker image load -i my_image.tar
  ```