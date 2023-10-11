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

- [Prerequisites](#prerequisites)
- [Sample React Application](#sample-react-application)
- [Launching instance on AWS](#launching-instance-on-aws)
- [Jenkins Installation](#jenkins-installation)
- [Docker Installation](#docker-installation)
- [Git Installation and cloning the GitHub repo](#git-installation-and-cloning-the-github-repo)
- [Nginx Installation](#nginx-installation)
- [Jenkins Setup](#jenkins-setup)
- [Creating Pipeline](#creating-pipeline)
- [setup of GitHub hook trigger for GITScm polling](#setup-of-github-hook-trigger-for-gitscm-polling)
- [Pipeline](#pipeline)

## Prerequisites

* An AWS EC2 Instance with installed jenkins, Docker, Nginx, and Git on it.
* A sample React application Code on a GitHub Repo.
* Basic knowledge of npm, AWS,  Jenkins, Docker, Git, and Nginx.

## Sample React Application

I have created a sample React Application: https://github.com/GirishAgarwal007/react.git and
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
- Step 10: port 22,80,443,8080,3000,3001 must be allowed in security group that you have attached with instance.
- Step 11: Take SSH Session of created instance 

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

## Git Installation and cloning the GitHub repo

Git is a distributed version control system that tracks changes in any set of computer files, usually used for coordinating work among programmers who are collaboratively developing source code during software development. Its goals include speed, data integrity, and support for distributed, non-linear workflows (thousands of parallel branches running on different computers).

```bash
# install git 
sudo apt-get install git -y 
```
```bash
# Verify installation
sudo git version
```
* You can fork this repo to your GitHub account to enable the feature of GitHub hook trigger for GITScm polling.
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

## Jenkins Setup

- Step 1: Open any web browser and search "http://public-ip-of-your-instance:8080"
- Step 2: Unlock Jenkins
	  Enter the password provided by jenkins at "/var/lib/jenkins/secrets/initialAdminPassword"
- Step 3: Customize Jenkins
	  Select "Install suggested plugins"
- Step 4: Create First Admin User
	  Enter details -----> click on "Save and Continue"
- Step 5: Instance Configuration
	  click on "Save and Finish"
- Step 6: Jenkins is ready!
	  click on "Start using Jenkins"

## Creating Pipeline

- Step 1: Click on "New Item"
- Step 2: Enter an item name and select "Pipeline" projct and click on "OK"
- Step 3: Provide a Description
- Step 4: "Enable project-based security" in general section if you want to give permissions to another jenkins users regarding this Item
- Step 5: Select "GitHub hook trigger for GITScm polling" to get your pipeline triggered automatically if there is change in code, see this ## setup of GitHub hook trigger for GITScm polling 
- Step 6: Provide pipeline syntax(groovy)
- Step 7: Click on "Save"

## setup of GitHub hook trigger for GITScm polling

When Jenkins receives a GitHub push hook, GitHub Plugin checks to see whether the hook came from a GitHub repository which matches the Git repository defined in SCM/Git section of this job. If they match and this option is enabled, GitHub Plugin triggers a one-time polling on GITScm. When GITScm polls GitHub, it finds that there is a change and initiates a build.

- Step 1: Go to your GitHub repo
- Step 2: Click on "Settings" tab 
- Step 3: Click on "Webhooks" under the "Code and automation" section
- Step 4: Click on "Add webhook"
- Step 5: Enter "Payload URL:" http://public-ip-of-your-instance:8080/github-webhook/
- Step 6: Click on "Add webhook"

## Pipeline 

Jenkins Pipeline is a suite of plugins which supports implementing and integrating continuous delivery pipelines into Jenkins. Written in Groovy Syntax. There are two types of Pipeline, one is "Scripted Pipeline" and second is "Declarative Pipeline". Our Pipeline is a  Scripted Pipeline.

```bash
node {
    try {
        stage('Pull the Source Code from GitHub') { 
        git branch: 'main', url: 'https://github.com/GirishAgarwal007/react.git'
    }
    stage("Dockerize the application") {
        sh '''sudo docker build -t react:pipeline .
              sudo docker stop app1
              sudo docker run --rm -dit --name app1 -p 3000:3000 react:pipeline
              sleep 20
              sudo docker stop app2
              sudo docker run --rm -dit --name app2 -p 3001:3000 react:pipeline
              sudo systemctl restart nginx'''
            }
            if (currentBuild.result == 'UNSTABLE') {
            emailext body: '''$PROJECT_NAME - Build # $BUILD_ID is UNSTABLE Triggered by - $BUILD_USER :

Check console output at $BUILD_URL to view the results.''', subject: '$PROJECT_NAME - Build # $BUILD_ID ', to: 'girish.ongraph@gmail.com'
    
        slackSend color: "warning", message: "${env.JOB_NAME} # ${env.BUILD_ID} is UNSTABLE Triggered by ${env.BUILD_USER} (<${env.BUILD_URL}console|click here to view the console output>)"
        } else {
            emailext body: '''$PROJECT_NAME - Build # $BUILD_ID is SUCCESS Triggered by - $BUILD_USER :

Check console output at $BUILD_URL to view the results.''', subject: '$PROJECT_NAME - Build # $BUILD_ID ', to: 'girish.ongraph@gmail.com'
    
        slackSend color: "good", message: "${env.JOB_NAME} # ${env.BUILD_ID} is SUCCESS Triggered by ${env.BUILD_USER} (<${env.BUILD_URL}console|click here to view the console output>)"
        }
        } catch (e) {
            emailext body: '''$PROJECT_NAME - Build # $BUILD_ID is FAILED Triggered by - $BUILD_USER :

Check console output at $BUILD_URL to view the results.''', subject: '$PROJECT_NAME - Build # $BUILD_ID ', to: 'girish.ongraph@gmail.com'
    
        slackSend color: "danger", message: "${env.JOB_NAME} # ${env.BUILD_ID} is FAILED Triggered by ${env.BUILD_USER} (<${env.BUILD_URL}console|click here to view the console output>)"
        }
}
```


























