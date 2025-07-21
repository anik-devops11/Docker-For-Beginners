### 🛑 What is None Network in Docker?

The **None network** mode disables all networking for the container. It provides **complete network isolation** — no access to the internet, no communication with other containers, and no port exposure to the host.

**It is useful when:**

* You want complete network isolation.
* You’re debugging or running apps that don’t need any network.

---

### ✅ Step 1: Run a Container with `none` Network

```bash
docker run -it --rm --network none alpine sh
```

* `--network none`: Disables networking completely.
* `alpine`: A lightweight Linux image.
* `sh`:  Launches a shell for testing..

### ✅ Step 2: Try Pinging a Website

Inside the container, try:

```sh
ping google.com
```

You’ll get an error like:

```
ping: bad address 'google.com'
```


You’ll see it fails due to no internet connection.

---
