#TO DEPLOY A HELLO WORLD WEBPAGE

**Step 1: Create a Dockerfile**

Create a Dockerfile (e.g., `Dockerfile`) in your project directory with the following contents:

```Dockerfile
# Use the official Tomcat image as the base image
FROM tomcat:9.0

# Copy your "Hello, World!" HTML page to Tomcat's webapps directory
COPY index.html /usr/local/tomcat/webapps/ROOT/

# Optionally, you can expose the default Tomcat HTTP port (8080)
EXPOSE 8080

# Start Tomcat when the container is launched
CMD ["catalina.sh", "run"]
```

In this Dockerfile:

- We use the official Tomcat image from Docker Hub (`tomcat:9.0`) as the base image.
- We copy your "Hello, World!" HTML page (e.g., `index.html`) to Tomcat's webapps directory. By placing it in the `ROOT` directory, it will be the default application served by Tomcat.
- Optionally, we expose the default Tomcat HTTP port 8080 to allow incoming connections.
- You can add any additional configurations or environment variable settings as needed.

**Step 2: Create the "Hello, World!" HTML Page**

Create a simple HTML file named `index.html` with the following content:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Hello, World!</title>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>
```

Place this HTML file in the same directory as your Dockerfile.

**Step 3: Build the Docker Image**

Build the Docker image using the Dockerfile:

```shell
docker build -t my-hello-world-app .
```

- `-t my-hello-world-app` assigns a name and tag to your Docker image. You can choose a different name and tag if you prefer.

**Step 4: Run a Container from Your Image**

Run a container from the Tomcat image:

```shell
docker run -p 8080:8080 my-hello-world-app
```

- `-p 8080:8080` maps the Tomcat container's port 8080 to port 8080 on your host machine.
- `my-hello-world-app` should match the image name you specified when building the image.

# USING DOCKER COMPOSE
To achieve the same functionality as the `docker run -p 8080:8080 my-hello-world-app` command using Docker Compose, you can create a `docker-compose.yml` file with the following content:

```yaml
version: '3'

services:
  my-hello-world-app:
    image: my-hello-world-app
    ports:
      - "8080:8080"
```

In this `docker-compose.yml` file:

- `version: '3'` specifies the Docker Compose file version.
- `services` section defines the services to be run.

Under the `my-hello-world-app` service:

- `image: my-hello-world-app` specifies the Docker image to use for this service. Replace `my-hello-world-app` with the actual name of your Docker image if it's different.
- `ports` maps port 8080 from the container to port 8080 on the host machine, just like the `-p 8080:8080` flag in the `docker run` command.

Save this `docker-compose.yml` file in your project directory, and then you can start the Docker Compose stack with the following command:

```shell
docker-compose up
```

This command will start a container based on the `my-hello-world-app` image, exposing port 8080. You can access your "Hello, World!" web application by opening a web browser and going to `http://localhost:8080`.

To stop the Docker Compose stack, press `Ctrl + C` in the terminal where it's running.

Your Dockerized "Hello, World!" web application with Tomcat should now be running. You can access it by opening a web browser and going to `http://localhost:8080`. You'll see the "Hello, World!" message displayed in your browser.

This example demonstrates how to containerize a simple HTML webpage with Tomcat using Docker. You can further expand on this foundation to deploy more complex web applications.
