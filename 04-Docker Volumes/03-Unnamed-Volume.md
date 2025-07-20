# 🐳 Unnamed Volume

This guide walks you through using **unnamed Docker volumes**, where Docker auto-generates the volume name and manages it for you.

---

## 🎯 Objective

- Understand unnamed volumes
- Store data inside the volume
- Reuse the volume with a new container
- Verify data persistence

---

## ✅ Step 1: Run a Container with an Unnamed Volume

```bash
docker run -it -v /mydata ubuntu
```
Docker auto-creates a **volume** and mounts it to `/mydata` in the container.

🔍 **Explanation:** <br>
`-v /mydata`  : The `-v /mydata` option tells Docker to create a storage space (called a volume) and connect it to the `/mydata` folder inside the container. Since no name is given, Docker creates the volume automatically and manages it in the background. Anything you save in the `/mydata` folder will be kept safe even if you stop or delete the container. This is an easy way to make sure your container's data doesn't get lost. `Ubuntu` is a image name.

## ✅ Step 2: Create a File Inside the Volume
Inside the container terminal:
```
cd /mydata
echo "This file is in an unnamed volume" > hello.txt
cat hello.txt
```
✅ Output:
```
This file is in an unnamed volume
```
🎯 You just created a file that is stored in the Docker-managed volume.

## ✅ Step 3: Exit the Container
```
exit
```
This stops and exits the container, but **the volume still exists.**

## ✅ Step 4: List All Docker Volumes
```
docker volume ls
```
📌 Look for a volume with a random name like:
<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/volume list.png" border="0">