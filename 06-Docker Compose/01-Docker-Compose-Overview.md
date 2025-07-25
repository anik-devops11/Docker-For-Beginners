# 🐳 What is Docker Compose?

**Docker Compose** is a tool that lets you **define and run multi-container Docker applications** easily.

Instead of running multiple `docker run` commands for each container, you use **one YAML file (`docker-compose.yml`)** to configure **services**, **networks**, and **volumes**, and then start everything with a single command.

---

### ✅ Why Use Docker Compose?

* 🔄 **Manages multiple containers** in one file (e.g., app + database)
* 🧪 **Simplifies development** workflows
* ⚙️ **Reusable configuration** (version-controlled YAML)
* ⛓️ **Defines dependencies** between services

---

### ⚙️ Common Commands

| Command                  | Description                               |
| ------------------------ | ----------------------------------------- |
| `docker compose up`      | Starts all containers                     |
| `docker compose up -d`   | Starts in detached mode                   |
| `docker compose down`    | Stops and removes containers & network    |
| `docker compose down -v` | Also removes named volumes (⚠️ Data loss) |
| `docker compose ps`      | Lists running services                    |
| `docker compose logs`    | Shows service logs                        |

---
