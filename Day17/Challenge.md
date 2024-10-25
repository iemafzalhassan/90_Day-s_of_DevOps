# Challenge Day 17:

---

### Current Status
- **Day Completed**: 17
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---
## Day 17: Docker Project for DevOps Engineers


### **Key Docker Jargons and Terms:**

#### 1. **Dockerfile**
A Dockerfile is a text file with a series of instructions that Docker uses to create an image. It’s essentially a blueprint for how your container is built. The Dockerfile contains commands to set up the operating system, install dependencies, copy files, and define how the containerized application should run.

##### Dockerfile Example:
```dockerfile
# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the current directory contents into the container at /usr/src/app
COPY . .

# Install any necessary dependencies
RUN npm install

# Make port 8080 available to the world outside this container
EXPOSE 8080

# Define the command to run the app
CMD ["node", "app.js"]
```

##### Real-world analogy:
Think of a Dockerfile as a recipe for baking a cake. It has all the ingredients (dependencies) and steps (commands) to create the final product (a container). Each layer added to the container is like adding an ingredient to the recipe.

#### 2. **Docker Image**
A Docker image is a read-only template that includes everything needed to run an application. It’s created from the Dockerfile. Think of the image as a snapshot of your application in a specific state. 

##### Real-world analogy:
Consider a Docker image like a "blueprint" or a "frozen meal" — it's pre-packaged and can be used to replicate the same setup across different machines.

#### 3. **Docker Container**
A container is a runtime instance of a Docker image. It’s a lightweight, standalone, executable package that includes everything needed to run the application.

##### Real-world analogy:
If the image is a blueprint or a frozen meal, the container is the actual building or the meal once it’s heated and ready to serve. It’s the running instance of your application.

#### 4. **Docker Hub**
Docker Hub is a cloud-based registry where you can store and share Docker images. You can push your custom images to Docker Hub or pull images created by others.

##### Real-world analogy:
Docker Hub is like GitHub for containers. It’s where developers store their code and allow others to download or use it.

---

### **Project Overview from myGitHub Repo:**
Your Docker projects showcase a range of web applications, containerized for consistent deployment. Let’s go over each:

1. **2048 Game**  
   - **Link to Repo**: [2048-game Docker Project](https://github.com/iemafzalhassan/Docker-for-DevOps/tree/main/2048-game)
   - **Link to DockerHub**: [2048-game Docker Project](https://hub.docker.com/repository/docker/iemafzal/2048-game/general)
   - **Description**: You created a Dockerfile for the popular 2048 game, packaging it into a container to run the web-based game in a browser. 
   - **Dockerfile Goal**: Create a container image that builds and serves the game using an appropriate web server.

2. **Nginx Project (nginx-project-1)**  
   - **Link to Repo**: [nginx-project-1](https://github.com/iemafzalhassan/Docker-for-DevOps/tree/main/nginx-project-1)
    - **Link to DockerHub**: [nginx-project-2](https://hub.docker.com/repository/docker/iemafzal/nginx-project-1/general)
   - **Description**: You set up Nginx, a lightweight and high-performance web server, within a Docker container. 
   - **Dockerfile Goal**: Create an Nginx container that serves static content and expose the container’s port for access in a browser.

3. **Python Web App (python-project-2)**  
   - **Link to Repo**: [python-project-2](https://github.com/iemafzalhassan/Docker-for-DevOps/tree/main/python-project-2)
   - **Link to DockerHub**: [python-project-2](https://hub.docker.com/repository/docker/iemafzal/python-project-2/general)
   - **Description**: This project involves creating a simple Python-based web application inside a Docker container, which can be accessed from a browser.
   - **Dockerfile Goal**: Define the environment and dependencies required to run the Python app and make it accessible via HTTP.

4. **Simple Node.js App (simple-nodejs-people-info-app)**  
   - **Link to Repo**: [simple-nodejs-people-info-app](https://github.com/iemafzalhassan/Docker-for-DevOps/tree/main/simple-nodejs-people-info-app)
   - **Link to DockerHub**: [simple-nodejs-people-info-app](https://hub.docker.com/repository/docker/iemafzal/simple-nodejs-people-info-app/general)
   - **Description**: A simple application built using Node.js that displays people's information.
   - **Dockerfile Goal**: Containerize the Node.js application and make sure it’s running correctly within the container.

---

### **Steps for the Task**

#### 1. **Create a Dockerfile**
You’ll start by creating a `Dockerfile` for each of your projects:

- For **Node.js** projects, ensure that the base image, dependencies, and app commands are defined.
- For **Python** apps, the Dockerfile should include the Python runtime, along with any dependencies (like Flask).
- For the **2048-game** or **Nginx-project-1**, ensure that the Dockerfile includes Nginx as the web server and serves the content.

##### Dockerfile Example (Python App):
```dockerfile
# Use an official Python runtime as the base image
FROM python:3.8-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Install necessary dependencies
RUN pip install -r requirements.txt

# Expose the app on port 5000
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
```

#### 2. **Build the Image Using Dockerfile**
To create the image for your application:
```bash
docker build -t <image-name> .
```
This command will read your `Dockerfile` and build the image.

#### 3. **Run the Container**
After building the image, you can run it:
```bash
docker run -d -p 5000:5000 <image-name>
```
Here, `-d` runs the container in detached mode (in the background), and `-p 5000:5000` maps port 5000 on the container to port 5000 on the host.

##### Flags Breakdown:
- `-d` (detached mode): Runs the container in the background.
- `-p` (port mapping): Exposes the specified port from the container to the host.
- `--name`: Assigns a name to the container.

#### 4. **Access the Application**
Open your web browser and visit `http://localhost:5000` (or the port you exposed). This verifies that the application inside the Docker container is running.

#### 5. **Push the Image to Docker Hub**
Once your image is working, you can push it to Docker Hub for others to use:
```bash
docker login
docker tag <image-name> <dockerhub-username>/<repository-name>
docker push <dockerhub-username>/<repository-name>
```

---


Keep practicing to enhance your skills, and feel free to check out the repository for more examples and real-world Docker projects: [Docker-for-DevOps Repo](https://github.com/iemafzalhassan/Docker-for-DevOps)