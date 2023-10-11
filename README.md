# Summary

This project demonstrates how to deploy a React application within a Docker Container using a Dockerfile and Jenkins, with the Nginx Server configured on the local system for serving React application.

## Description

This project provides a step-by-step guide to deploy a React application within a Docker Container. The Deployment process is automated with Jenkins Pipeline to ensure continuous integration (Zero Downtime), and the Nginx server, which serves the React application, is configured on the local system.   
Our pipeline workflow:
 
- As you push your code to the GitHub repository that is configured with CircleCI.
- CircleCI build will triggered and our pipeline will run.
- First, it builds the docker image.
- Second, it runs a container from that image.
- sleep for 15s.
- Then, runs another container.


## Table of Contents

- [Prerequisites](#prerequisites)  
- [Launching an EC2 instance on AWS](#launching-ec2-instance-on-aws)
- [Jenkins Installation](#jenkins-installation)
- [Docker Installaion](#docker-installation)
- [Git Installation](#git-installation)
- [Nginx Installation](#nginx-installation)

## Prerequisites

* An AWS EC2 Instance with installed jenkins, Docker, Nginx, and Git on it.
* An another server where a sample React application Code is available .
* Basic knowledge of Jenkins, Docker, Git, and Nginx.
