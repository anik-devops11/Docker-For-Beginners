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

# 🐳 Named Volume with MySQL

This guide demonstrates how to use **Docker Volumes** to persist and serve custom content using an Nginx container.

---

## ✅ Step-by-Step Commands with Explanation

### 📦 1. Create a Docker Volume

```
docker volume create mysql-data
```
Creates a named volume `mysql-data` to store website files outside the container.

### 📋 2. List All Docker Volumes

```
docker volume ls
```
### ⬇️ 3. Pull the MySql Docker Image

```
docker pull mysql:8
```

### 🚀 4. Run the MySql Container with Volume and Port Mapping

#### For Windows Users
```
docker run -d --name my-nginx -p 9090:80 -v nginx-data:/usr/share/nginx/html nginx
```
or 
```
docker run -d `
--name my-mysql `
-e MYSQL_ROOT_PASSWORD=admin123 `
-e MYSQL_DATABASE=testdb `
-v mysql-data:/var/lib/mysql `
-p 3306:3306 `
mysql:8
```

#### For Linux/macOS Users

```
docker run -d \
  --name my-mysql \
  -e MYSQL_ROOT_PASSWORD=admin123 \
  -e MYSQL_DATABASE=testdb \
  -v mysql-data:/var/lib/mysql \
  -p 3306:3306 \
  mysql:8
```

**Explanation:**

| Option                            | Purpose                                |
| --------------------------------- | -------------------------------------- |
| `--name my-mysql`                 | Name of the container                  |
| `-e MYSQL_ROOT_PASSWORD=admin123` | Set root password                      |
| `-e MYSQL_DATABASE=testdb`        | Creates a database named `testdb`      |
| `-v mysql-data:/var/lib/mysql`    | Mount volume to MySQL’s data directory |
| `-p 3306:3306`                    | Expose MySQL port 3306 (default)       |
| `mysql:8`                         | Image to run                           |

### 📝 5. Verify the Container is Running

```
docker ps
```

Check that `my-mysql` is running and listening on port **3306.**

### 📁 6. Connect to the MySQL Container
Use the MySQL client inside the container:

```
docker exec -it my-mysql mysql -uroot -p
```
Enter password `admin123`.

Once inside the MySQL shell, run:
```
SHOW DATABASES;
```
You should see `testdb` listed. <br>
Create a test table:
```
USE testdb;
CREATE TABLE users (id INT PRIMARY KEY, name VARCHAR(50));
INSERT INTO users VALUES (1, 'Anik'), (2, 'Dash');
SELECT * FROM users;

```
Exit MySQL:
```
exit
```
### 🛑 7. Stop and Remove the Container (Keep Volume)r

```
docker stop my-mysql
docker rm my-mysql
```
Data is still safe in the `mysql-data` volume!

### 🔁 8. Run MySQL Again Using the Same Volume
```
docker run -d `
--name my-mysql `
-e MYSQL_ROOT_PASSWORD=admin123 `
-e MYSQL_DATABASE=testdb `
-v mysql-data:/var/lib/mysql `
-p 3306:3306 `
mysql:8

```
You didn’t need to recreate the database — it’s still there!<br>
Use docker exec -it `my-mysql mysql -uroot -p` to check.
```
USE testdb;
SELECT * FROM users;
```
✔️ Your data is still present!

### 🧹 9. Cleanup (Optional)
```
docker stop my-mysql
docker rm my-mysql
docker volume rm mysql-data
```
This removes everything: container + volume + data.