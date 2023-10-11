# Summary

This project demonstrates how to deploy a React application within a Docker Container using a Dockerfile and Jenkins, with the Nginx Server configured on the local system for serving React application.

## Description

This project provides a step-by-step guide to deploy a React application within a Docker Container. The Deployment process is automated with Jenkins Pipeline to ensure continuous integration (Zero Downtime), and the Nginx server, which serves the React application, is configured on the local system. I used AMI "Ubuntu 22.04" and instance type "t2.medium" for this project.
  
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

- Step 1: Create an AWS account/ Login if have already
- Step 2: Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/ 
- Step 3: Click on "Launch instance"
- Step 4: Choose an Amazon Machine Image (AMI) (ex: Ubuntu 22.04)
- Step 5: Choose an Instance Type (ex: t2.medium)
- Step 6: Select key Pair/ Creat new if not available
- Step 7: Configure Network Settings (Select VPC an Security Group)
- Step 8: Configure Storage
- Step 9: Click on "Launch instance"
- Take SSH Session of created instance 

## Jenkins Installation
 

