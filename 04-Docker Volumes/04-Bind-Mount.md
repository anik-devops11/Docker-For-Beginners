# 🐳 Docker Bind Mount 

This guide shows how to use **Docker bind mounts** to share a folder between your host machine and a Docker container. This allows real-time file sharing — changes in the host folder are reflected inside the container and vice versa.

---

## 🎯 What You’ll Learn

- How to mount a folder from the host into a Docker container
- How to create and access shared files from both sides
- Understand how bind mounts differ from named volumes

---

## 🧠 What is a Bind Mount?
A **Bind mount** lets you link a folder from your local computer (host) into a Docker container. This is helpful when:

- You want to develop code locally but test it in a container.

- You need real-time file sync between your PC and the container.

- You want to avoid copying files in and out manually.

## 🧱 Step-by-Step Instructions

### ✅ Step 1: Create a Folder on Your Host

```
mkdir <Your_Path>
```
Example:
```
mkdir D:\docker-bind
```
📌 Replace `D:` with another drive if needed.

### ✅ Step 2: Add a File to the Folder (Optional) 
```
echo "Hello from host!" > D:\docker-bind\hello.txt
```

### ✅ Step 3: Run a Container with Bind Mount
```
docker run -it --name <Names_the_container > `
  -v <Path> `
  <Image_name>
```
Example :
```
docker run -it --name test-bind `
  -v D:/docker-bind:/data `
  ubuntu
```
⚠️ Use forward slashes (/) in the Docker command, even on Windows.

### ✅ Step 4: Inside the Container

```
cd /data
ls
cat hello.txt
```
If you follow **Step 2**, you will see `Hello from host!`.

### ✅ Step 5: Create a File from the Container
```
echo "Hello from container!" > container.txt
```
### ✅ Step 6: View the File from Host (Windows)
Go to `D:\docker-bind` and verify that `container.txt` exists — created from within the container.
### ✅ Step 7: Exit the Container
```
exit
```
### ✅ Step 8: Clean Up (Optional)
To remove the container and the test folder:
```
docker rm test-bind
Remove-Item -Recurse -Force D:\docker-bind
```

## 📘 Final Notes

- Always use **full path** for the host side.
- The host folder **must exist** before running the container.
- The container path (like `/data`) will be created automatically by Docker if it doesn't exist.
- Always use forward slashes `/` for bind mount paths in Docker commands.