# Summary

This project demonstrates how to deploy a React application within a Docker Container using a Dockerfile and Jenkins, with the Nginx Server configured on the local system for serving React application.

## Description

This project provides a step-by-step guide to deploy a React application within a Docker Container. The Deployment process is automated with Jenkins Pipeline to ensure continuous integration (Zero Downtime), and the Nginx server, which serves the React application, is configured on the local system. I used AMI "Ubuntu 22.04" and instance type "t2.medium" for this project.
  
## Pipeline Workflow:
 
- As you push your code to the GitHub repository, The GitHub Webhook will trigger the Jenkins Pipeline.
- Jenkins build will be triggered and the pipeline will run.
- Initially, it builds a docker image using Dockerfile.
- Then, it will launch a Docker containers using that image.
- sleep for 20s.
- Then, another container will be launched using same image.


## Table of Contents

- [Sample React Application](#smaple-react-application)
- [Prerequisites](#prerequisites)  
- [Launching instance on AWS](#launching-instance-on-aws)
- [Jenkins Installation](#jenkins-installation)
- [Docker Installation](#docker-installation)
- [Git Installation](#git-installation)
- [Nginx Installation](#nginx-installation)

## Prerequisites

* An AWS EC2 Instance with installed jenkins, Docker, Nginx, and Git on it.
* A sample React application Code on a GitHub Repo.
* Basic knowledge of npm, AWS,  Jenkins, Docker, Git, and Nginx.

## Sample React Application

I have created a sample React Application: https://github.com/GirishAgarwal007/react.git
Dockerfile is also available in this repo.

## Launching instance on AWS

The Amazon Web Services (AWS) platform provides more than 200 fully featured services from data centers located all over the world, and is the world's most comprehensive cloud platform.

- Step 1: Create an AWS account/ Login if have already
- Step 2: Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/ 
- Step 3: Click on "Launch instance"
- Step 4: Choose an Amazon Machine Image (AMI) (ex: Ubuntu 22.04)
- Step 5: Choose an Instance Type (ex: t2.medium)
- Step 6: Select key Pair/ Creat new if not available
- Step 7: Configure Network Settings (Select VPC an Security Group)
- Step 8: Configure Storage
- Step 9: Click on "Launch instance"
- Step 10: Take SSH Session of created instance 

## Jenkins Installation

Jenkins is an open source continuous integration/continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.


Follow the official document:
  https://www.jenkins.io/doc/book/installing/linux/ 

```bash
# installing jenkins 
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```
```bash
# Verify the installation
  sudo jenkins --version
```
```bash
# Start Jenkins 
  sudo systemctl start jenkins
```
```bash
# Enable Jenkins
  sudo systemctl enable jenkins
```
```bash
# Check status of Jenkins
  sudo systemctl status jenkins
```
## Docker Installation

Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime.

Follow the official document:
  https://docs.docker.com/engine/install/ubuntu/

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
```bash
# Install the latest version:
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
```bash
# Verify the installation
sudo docker --version
```
```bash
# Start Docker
sudo systemctl start docker
```
```bash
# Enable Docker
sudo systemctl enable docker
```
```bash
# Check status of Docker
sudo systemctl status docker
``` 

## Git Installation

Git is a distributed version control system that tracks changes in any set of computer files, usually used for coordinating work among programmers who are collaboratively developing source code during software development. Its goals include speed, data integrity, and support for distributed, non-linear workflows (thousands of parallel branches running on different computers).

```bash
# install git 
sudo apt-get install git -y 
```
```bash
# Verify installation
sudo git version
```
```bash
# Clone the provided GitHub repo
sudo git clone https://github.com/GirishAgarwal007/react.git
```

## Nginx Installation

Nginx is a web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.

Follow the Official document:
https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/

```bash
# Update the Ubuntu repository information
sudo apt-get update
```
```bash
# Install Nginx
sudo apt-get install nginx
```
```bash
# Verify the installation
sudo nginx -v
```

## 






























