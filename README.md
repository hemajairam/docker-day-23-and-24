# docker-day-23-and-24
 Getting Started with Docker: My Hands-on Experience
 
* Installing Docker on an AWS EC2 Ubuntu instance
* Writing a Dockerfile to create custom Docker images
* Running containers and pushing images to Docker Hub
  
🔹 Installing Docker on an AWS EC2 Instance

  To set up Docker, simply run
  
    sudo apt update  
    sudo apt install docker.io -y  

  Then, start the Docker service:
  
    sudo systemctl start docker  
    sudo systemctl enable docker 

🔹 Avoiding Common Issues

 common issue i faced  while running Docker commands. If you see something like:


    Got permission denied while trying to connect to the Docker daemon socket.

  
To check whether Docker is running on your system

    sudo systemctl status docker


add your user to the Docker group

    sudo usermod -aG docker $USER  

  (Logout and log back in for changes to take effect.)
  

🔹 Writing a Dockerfile & Creating an Image

    FROM ubuntu:latest  
    WORKDIR /app
    COPY . /app 
    RUN apt-get update && apt-get install -y python3 python3-pip  
    CMD ["python3", "app.py"] 
    
To build and tag the image:

    docker build -t username/my-first-docker-image:latest

To verify:

    docker images  

🔹 Running & Pushing to Docker Hub

    docker run -it username/my-first-docker-image
    Hello world

 After testing my container, I pushed it to Docker Hub

    docker login  
    docker push my-dockerhub-username/my-first-docker-image:latest



