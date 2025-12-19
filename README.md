# DevOps CI/CD Pipeline Project
This project demonstrates an end-to-end CI/CD pipeline using GitHub, Jenkins, and Docker on AWS EC2.
The pipeline automates application build and deployment using Docker containers, triggered through Jenkins.

🛠️ Tools & Technologies Used

AWS EC2 – Server hosting

GitHub – Source code management

Jenkins – CI/CD automation

Docker – Containerization

Nginx – Web server

# index.html
<h1>Hello from DevOps </h1>

# Dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html/index.html

# jenkins file
pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 80:80 myapp || true'
            }
        }
    }
}

# Launch AWS EC2

  Amazon Linux 2

Open ports: 22, 80, 8080

# This single command installs 3 important tools needed for your DevOps project.

yum install git docker java-17-amazon-corretto -y

# Jenkins Setup

Access Jenkins: http://<EC2-PUBLIC-IP>:8080

Install suggested plugins

Create a Pipeline job

Connect GitHub repository


 # Application Access

Open browser:

http://<EC2-PUBLIC-IP>

Issues Faced & Resolution

 # Issue: Jenkins could not access Docker daemon
Solution: Added Jenkins user to Docker group and restarted services.

sudo usermod -aG docker jenkins
sudo systemctl restart docker
sudo systemctl restart jenkins
