## Associate Training and Hands-on for creating a website using Docker, HTML and Nginx: Beginner ##

(Rough Draft)

Before beginning the hands-on lab, please review the concepts below for a clear understanding. Feel free to use the resources listed or research on your own. 

**Docker Basics**
- Understanding containers vs virtual machines
- Installing Docker Desktop
- Docker architecture: images, containers, registries
- Running your first container
- Docker commands: run, ps, stop, rm, images

**Building Docker Images**
- Understanding Dockerfiles
- Creating custom images
- Multi-stage builds
- Image optimization and layer caching
- Tagging and versioning images

**Resources:**

- Docker installation: https://docs.docker.com/engine/install
- DockerFile Basics: https://www.geeksforgeeks.org/cloud-computing/what-is-dockerfile/
- HTML Basics: https://www.w3schools.com/html/html_intro.asp
- Vi: https://www.redhat.com/en/blog/introduction-vi-editor
- Nano: https://www.howtogeek.com/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/
- What are containers: https://www.docker.com/resources/what-container/ 


## Hands-On Lab - Nginx Website with Docker
**Objective:** Deploy a simple static website using Nginx in a Docker container
**Tools Needed:**
- Docker
- Terminal basics
- GitHub
- Git
- Text File Editor: nano, vi, etc... 

**Instructions:**

**1. Create Project Directory**

```
mkdir nginx-docker-demo
cd nginx-docker-demo
```
**2. Create a Simple HTML Website**

```
nano index.html
```

Add the followng HTML code for the file

```
{
<!DOCTYPE html>
<html>
<head>
    <title>DevOps Training Demo</title>
</head>
<body>
    <h1>Welcome to My Dockerized Website!</h1>
    <p>This is running in an Nginx container.</p>
</body>
</html>
}
```

**Note** Make sure you have the Docker Application running before continuing the next steps

**3. Create a Dockerfile in the project root and add the following code:**

```
nano Dockerfile
```
```
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
```
**4. Build the Docker Image**

```
docker build -t my nginx-website:v1
```

**5. Run the Container**

```
docker run -d -p 8080:80 --name my-website my-nginx-website:v1
```
**6. Test the website**

```
http://localhost:8080
```
You should see a static webpage that displays: Welcome to My Dockerized Website!
This is running in an Nginx container.

**7. Inspect and Manage**

```
docker ps - checks running containers
docker ps -a  - checks all containers, running or not
docker logs my-website - checks logs of that particular container
docker stop my-website
docker rm my-website
```
**Notes:** 
- Everytime you change the Dockerfile for this project, you need to stop the container, make the changes, and run the build command and then the run command shown above
- If you know HTML, feel free to create a more in depth website following these steps
  





