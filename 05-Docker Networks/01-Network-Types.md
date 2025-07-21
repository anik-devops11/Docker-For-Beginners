# 🐳 What is Docker Network?
Docker Network is a system that allows Docker containers to communicate with each other and with external systems. It provides a way to manage how containers connect to one another and to the outside world, offering both isolation and connectivity.

---

## 🔗 Types of Docker Networks:

### Bridge Network
This is the default network type used when you start containers without specifying a network. It's ideal for standalone applications running on a single Docker host. Containers on the same bridge network can communicate with each other using container names.

### Host Network
In this mode, the container shares the host machine's network stack. There's no isolation between the host and the container's network, which can improve performance but reduces security.

### None Network
This completely disables networking for the container. It's useful when you want to run a container with no external network access.