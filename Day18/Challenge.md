# Challenge Day 18:

---

### Current Status
- **Day Completed**: 18
- **Total Days in Challenge**: 90

Join #TrainWithShubham Community on an exhilarating journey of learning and growth as we embark on the #90DaysofChallenge!

---

## Day 18: Docker Compose for DevOps Engineers

### **What is Docker Compose?**

Imagine you’re setting up a movie night with friends. You have different tasks: one friend brings the snacks, another handles the projector, and someone else sets up the seating. You need them to work together in sync for the night to be perfect. Now, think of **Docker Compose** as the party planner who coordinates everything to ensure each task is handled correctly at the right time.

In the same way, **Docker Compose** helps you manage applications that have multiple parts, like a web app with a database and an API service. Instead of starting each service manually, Docker Compose uses a special file (called `docker-compose.yml`) to set everything up for you automatically. 

---

### **What is YAML?**

Before we jump further, let's quickly talk about **YAML**. YAML is like writing a shopping list in a notebook—simple and easy to understand. It's a human-readable format used for configuring stuff, and it's perfect for defining services in Docker Compose. 

**YAML Example** (our shopping list for containers 😉):
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: password123
```
In this example, we’re setting up two services:
1. A **web service** using Nginx (that listens on port 8080).
2. A **db service** using MySQL with a predefined password.

---

### **Real-World Scenario: Microservices Architecture Explained**

Now, let’s take a moment to understand **microservices**. Imagine you’re at a fast-food restaurant. Instead of having one person do everything (take your order, cook, prepare drinks), there’s a specialized team:
- One person takes your order (this could be your **frontend service**).
- Another person handles the cooking (this is your **backend service**).
- Another worker takes care of drinks (this could be a **database service**).

Each one of these “services” is like a microservice in an app—they focus on one specific task and work independently. **Docker Compose** allows you to set up and run these microservices smoothly without having to manage each one individually.

---

### **Docker Compose (`docker-compose.yml`)**

The `docker-compose.yml` file is the heart of Docker Compose. It’s like the game plan for your entire multi-container application.

Let’s break down what’s inside:

1. **Version**: This tells Docker which version of Docker Compose you’re using (currently version 3 is the most common).
   
2. **Services**: These are the different components (containers) of your application. It could be a database, a web server, or even a caching service.

3. **Ports**: This is where you tell Docker which ports on your computer should be connected to the services running inside the containers.

4. **Environment Variables**: These are like settings for your service. For example, setting a password for your database.

---

### **Sample `docker-compose.yml` File**:

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
    networks:
      - app-network

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: supersecretpassword
    ports:
      - "3306:3306"
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - app-network

volumes:
  db_data:

networks:
  app-network:
```

#### **How to run this?**:
1. Save this file as `docker-compose.yml`.
2. Run the command:
   ```bash
   docker-compose up
   ```
3. Docker will pull the images, create the containers, and spin up the services. Your web server (Nginx) will be accessible on **http://localhost:8080**, and MySQL will be running in the background.

### **Let’s break down the example**:
- **Web service**: This runs Nginx, which is like the guy taking orders in our restaurant analogy. We’re exposing it on port 8080 of your machine.
- **DB service**: This is your database (like the cook in the kitchen). It stores and serves your app’s data.
- **Volumes**: Volumes are like permanent storage. Even if the container shuts down, your data is saved.

---

### **Task 2: Pull a Docker Image and Run it**

1. **Pull an Image**:
   Grab an image from Docker Hub. In our example, let’s pull Nginx:
   ```bash
   docker pull nginx
   ```

2. **Run the Container**:
   Once pulled, run it using this command:
   ```bash
   docker run -d -p 8080:80 --name web-server nginx
   ```

   - **-d**: Runs the container in detached mode (in the background).
   - **-p 8080:80**: Maps port 80 inside the container to port 8080 on your local machine.
   - **--name**: Names the container "web-server" for easy reference.

3. **Inspect the Container**:
   If you want to see details of the running container, use:
   ```bash
   docker inspect web-server
   ```

4. **Check the Logs**:
   If something goes wrong, or if you want to check what the container is doing, check the logs:
   ```bash
   docker logs web-server
   ```

5. **Stop and Start the Container**:
   You can stop the container using:
   ```bash
   docker stop web-server
   ```

   And start it again with:
   ```bash
   docker start web-server
   ```

6. **Remove the Container**:
   Once you're done, you can remove the container:
   ```bash
   docker rm web-server
   ```

---

### **Why Docker Compose is Important for DevOps?**

- **Simplicity**: Docker Compose simplifies running applications with multiple services. You don’t have to manually start each service. Just define them in a `docker-compose.yml` file and start them all at once.
  
- **Consistency**: Whether you’re developing locally or deploying to production, Compose ensures that your environment is always the same. No more “it works on my machine” excuses!

- **Microservices Architecture**: Compose allows you to manage microservices effortlessly, ensuring that all your services (containers) communicate correctly.

---

#### **Check out our other Docker projects on GitHub**:
Feel free to explore and contribute to my Docker projects [here](https://github.com/iemafzalhassan/Docker-for-DevOps).

---