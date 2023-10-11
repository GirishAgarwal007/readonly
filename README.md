# Summary

This project demonstrates how to deploy a React application within a Docker Container using a Dockerfile and Jenkins, with the Nginx Server configured on the local system for serving React application.

## Description

This project provides a step-by-step guide to deploy a React application within a Docker Container. The Deployment process is automated with Jenkins Pipeline to ensure continuous integration (Zero Downtime), and the Nginx server, which serves the React application, is configured on the local system.   
## Our pipeline workflow:
 
- As you push your code to the GitHub repository, The GitHub Webhook will trigger the Jenkins Pipeline.
- Jenkins build will be triggered and the pipeline will run.
- Initially, it builds a docker image using Dockerfile.
- Then, it will launch a Docker containers using that image.
- sleep for 20s.
- Then, another container will be launched using same image.


## Table of Contents

- [Prerequisites](#prerequisites)  
- [Launching an EC2 instance on AWS](#launching-ec2-instance-on-aws)
- [Jenkins Installation](#jenkins-installation)
- [Docker Installaion](#docker-installation)
- [Git Installation](#git-installation)
- [Nginx Installation](#nginx-installation)

## Prerequisites

* An AWS EC2 Instance with installed jenkins, Docker, Nginx, and Git on it.
* An another server where a sample React application Code is available and the code will be pushed to GitHub Repo.
* Basic knowledge of npm, AWS,  Jenkins, Docker, Git, and Nginx.

## Launching an EC2 instance on AWS

- Create an AWS account
- Login to that account
- Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/ .
- 
