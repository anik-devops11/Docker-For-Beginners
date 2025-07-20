# 🐳 What is a Docker Volume?

A **Docker Volume** is a way to **store data persistently** outside of the container's internal filesystem. Volumes are managed by Docker and are useful for saving:

- Application data
- Database files
- Logs and configs

Even if the container is deleted or recreated, the data in volumes **remains safe**.

---

## ❓ Why Do We Use Docker Volumes?

| Function                        | Explanation                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| ✅ **Persist Data**            | Data won't disappear when the container stops or is deleted.                |
| 🔄 **Share Data**             | Multiple containers can access the same data using a shared volume.         |
| 📂 **Store Configs or Logs**   | Great for storing config files, logs, or database files.                    |
| 🔧 **Backup & Restore**       | You can easily back up and restore your data.


---

## 📚 Types of Docker Volumes

### 1. 🕵️‍♂️ Unnamed Volume

- Created automatically by Docker if no name is given.
- Stored under Docker’s internal directory.
- Best for temporary or one-off containers.

**Example:**
```
docker run -v /app/data busybox
```

### 2. 🏷️ Named Volume

- Created and named by the user.
- Can be reused across containers.
- Easy to inspect and manage.

**Create Volume:**
```
docker volume create <Volume_Name>
```

Example

```
docker volume create mydata
```
**Use Volume:**
```
docker run -v mydata:/app/data busybox
```

**Inspect Volume:**
```
docker volume inspect mydata
```
### 3. 🗂️ Bind Mount
- Maps a specific host directory to the container.
- Full access to host files from the container.
- Great for development (live reload).

Example:
```
docker run -v $(pwd)/project:/app busybox
```

## 🔍 Handy Docker Volume Commands

| Command                      | Description              |
| ---------------------------- | ------------------------ |
| `docker volume create <Volume_Name>`  | Create a named volume    |
| `docker volume ls`           | List all volumes         |
| `docker volume <Volume_Name>` | View details of a volume |
| `docker volume rm <Volume_Name>`      | Remove a volume          |
| `docker volume prune`        | Remove unused volumes    |
