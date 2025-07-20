# 🐳 Unnamed Volume

This guide walks you through using **unnamed Docker volumes**, where Docker auto-generates the volume name and manages it for you.

---

## 🎯 Objective

- Understand unnamed volumes
- Store data inside the volume
- Reuse the volume with a new container
- Verify data persistence

---

### ✅ Step 1: Run a Container with an Unnamed Volume

```bash
docker run -it -v /mydata ubuntu
```
Docker auto-creates a **volume** and mounts it to `/mydata` in the container.

🔍 **Explanation:** <br>
`-v /mydata`  : The `-v /mydata` option tells Docker to create a storage space (called a volume) and connect it to the `/mydata` folder inside the container. Since no name is given, Docker creates the volume automatically and manages it in the background. Anything you save in the `/mydata` folder will be kept safe even if you stop or delete the container. This is an easy way to make sure your container's data doesn't get lost. `Ubuntu` is a image name.

### ✅ Step 2: Create a File Inside the Volume
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

### ✅ Step 3: Exit the Container
```
exit
```
This stops and exits the container, but **the volume still exists.**

### ✅ Step 4: List All Docker Volumes
```
docker volume ls
```
📌 Look for a volume with a random name like:

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/volume list.png" border="0">

### ✅ Step 5: Identify Which Volume Was Used
1. Find your container:
```
docker container ls -a
```
2. Inspect it:
```
docker container inspect <Container_ID>
``` 
3. In the output, find the `"Mounts"` section:

<img src="https://github.com/anik-devops11/Docker-For-Beginners/blob/main/Images/Mounts.png" border="0">

Now you know the actual volume name Docker created for `/mydata`.

### ✅ Step 6: Delete the Old Container

```
docker rm <container_id>
```
⚠️ This removes the container but not the volume.

### ✅ Step 7: Reuse the Same Volume in a New Container
```
docker run -it -v <volume_name>:/mydata ubuntu
```
👉 Replace `<volume_name>` with the one found in Step 5. 

Inside the new container:
```
cd /mydata
cat hello.txt
```
✅ You’ll see:
```
This file is in an unnamed volume
```
🎉 That proves your data is still there, even with the old container gone!

### 🧹 Step 8: (Optional) Delete the Volume

```
docker volume rm <volume_name>
```
📌 You can only remove a volume if no containers are using it.