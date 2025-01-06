# Building Custom Docker Images 🚀

This document walks you through creating a custom Docker image.
---

## **Project Structure** 📁

Create the following project structure:

```
custom-node-image/
├── server.js
├── Dockerfile
```

### **Initialize the Project** ⚙️

Before writing your code, run the following commands in the `custom-node-image` directory:

1. **Create a `package.json` file:**

   ```bash
   npm init -y
   ```

   This creates a `package.json` file to track your project dependencies.

2. **Install Express.js:**

   ```bash
   npm install express
   ```

   This command installs the `express` library and adds it as a dependency in the `package.json` file.

### **File: server.js** 📄

This is the Node.js application that displays the custom message:

```javascript
const express = require("express");
const app = express();
const PORT = process.env.PORT || 8000;

app.get("/", (req, res) => {
  return res.json({ message: "Hello, it is Custom Image!\n" });
});

app.listen(PORT, () => console.log(`Server started on PORT: ${PORT}`));
```

---

### **File: Dockerfile** 📄

The `Dockerfile` contains instructions to build the custom Docker image:

```dockerfile
# Use the official Node.js base image
FROM node:14

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy application files to the working directory
COPY . ./

# Install dependencies
RUN npm install

# Expose the application port
EXPOSE 8000

# Run the application
CMD ["node", "server.js"]
```

---

## **Building and Running the Docker Image** 🚀

### **Step 1: Build the Docker Image** 🏗️

Run the following command to build your Docker image:

```bash
docker build -t <image_name> .
```
- Here `.` means `Dockerfile` exist in the same file.
```bash
docker build -t custom-node-image .
```

### **Step 2: Verify the Image** 🔍

Check if the image was successfully created:

```bash
docker images
```

You should see `custom-node-image` in the list.

### **Step 3: Run the Docker Container** 🚢

Start a container from the custom image:

```bash
docker run -it -p <host_port>:<container_port> <image_name>
```

```bash
docker run -it -p 8000:8000 custom-node-image
```

### **Step 4: Access the Application** 🌐

Open your browser and navigate to:

```
http://localhost:8000
```

You should see the message:

```
Hello, it is Custom Image!
```

---

## Additional Tips 💡

`e` is indeed the command-line option used in Docker to set environment variables for a running container. By using `e` we will set custom port.

```
docker run -it -e PORT=[Set Custom Port No] -p <host_port>:<container_port> <image_name>
```

```
docker run -it -e PORT=9090 -p 1000:9090 custom-node-image
```

## **Summary**

In this tutorial, you learned how to:

- Create a simple Node.js application.
- Write a `Dockerfile` to build a custom Docker image.
- Build and run the image as a container.

This forms the foundation for deploying containerized applications using Docker. You can now expand this project with additional features or use it as a base for more complex setups.