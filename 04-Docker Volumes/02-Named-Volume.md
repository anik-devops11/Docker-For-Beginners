# 🐳 Named Volume with Nginx 

This guide demonstrates how to use **Docker Volumes** to persist and serve custom content using an Nginx container.

---

## ✅ Step-by-Step Commands with Explanation

### 📦 1. Create a Docker Volume

```
docker volume create <Volume_Name>
```

```
docker volume create nginx-data
```
Creates a named volume `nginx-data` to store website files outside the container.

### 📋 2. List All Docker Volumes

```
docker volume ls
```
### ⬇️ 3. Pull the Nginx Docker Image

```
docker pull nginx
```

### 🚀 4. Run the Nginx Container with Volume and Port Mapping
```
docker run -d --name my-nginx -p 9090:80 -v nginx-data:/usr/share/nginx/html nginx
```
Explanation:

| Option                                | Description                                  |
| ------------------------------------- | -------------------------------------------- |
| `-d`                                  | Detached mode (runs in background)           |
| `--name my-nginx`                     | Assigns a custom name to the container       |
| `-p 9090:80`                          | Maps host port `9090` to container port `80` |
| `-v nginx-data:/usr/share/nginx/html` | It’s the default directory inside the Nginx container where it looks for website files    |
| `nginx`                               | Uses the Nginx image                         |

🔗 Visit: `http://localhost:9090`

### 📝 5. Create a Custom HTML File

```
echo "<h1>Hello from Docker Volume!</h1>" > index.html
```

Creates a basic `index.html` file on your host system.

### 📁 6. Copy the HTML File into the Container Volume

```
docker cp index.html my-nginx:/usr/share/nginx/html/index.html
```

Replaces the default Nginx page with your custom HTML inside the container's mounted volume.

### 🛑 7. Stop and Remove the Container

```
docker stop my-nginx
docker rm my-nginx
```

Stops and deletes the container — but the volume and its data remain.

### 🔁 8. Recreate the Container with the Same Volume
```
docker run -d --name my-nginx -p 9090:80 -v nginx-data:/usr/share/nginx/html nginx
````

Restarts Nginx using the same volume.<br>
Your **custom HTML** will still be visible at `http://localhost:9090`

### 🧹 9. Cleanup (Optional)
```
docker stop my-nginx
docker rm my-nginx
docker volume rm nginx-data
del index.html  # For Windows: remove file from host
```