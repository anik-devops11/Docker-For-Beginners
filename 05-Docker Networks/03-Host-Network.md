## 🖧 Host Network in Docker

The **Host Network** removes the network isolation between the Docker container and the host. That means the container shares the `host’s network stack` directly — no virtual interface or NAT.

>  So, any port you expose inside the container is **directly available** on the host, without using `-p` port mapping.

---

### ✅ Key Characteristics

- No `-p` (port publishing) needed.
- The container uses the **host's IP address**.
- Fastest network performance (no NAT).
- Containers can conflict if they use the same ports.

---

### 🧪 Hands-On Practical (Linux Only)

Run an Nginx container using the host network:

```bash
docker run -d --name host-nginx --network host nginx
```
---

### 🧩 Command Breakdown

* `docker run` – Starts a new container.
* `-d` – Runs the container in detached mode (background).
* `--name host-nginx` – Assigns a name to the container.
* `--network host` – Shares the host’s network directly.
* `nginx` – Uses the official Nginx image (which listens on port 80).

---

### 🌐 Access

Once the container is running, open your browser or use `curl`:

```bash
http://localhost
```