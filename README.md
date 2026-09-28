##### Jenkins CI/CD Pipeline with GitHub, Docker & AWS EC2

## Overview

This project demonstrates a basic CI/CD pipeline using **GitHub, Jenkins, Docker, and AWS EC2**.

I created a Jenkins pipeline that automatically gets triggered when changes are pushed to the GitHub repository. 
Jenkins then retrieves the latest code, performs basic validation, builds a Docker image, and deploys the application as a Docker container.

## Workflow

GitHub
   ↓
GitHub Webhook
   ↓
Jenkins
   ↓
Checkout Code
   ↓
Test
   ↓
Build Docker Image
   ↓
Run Docker Container
   ↓
Application Deployment

What I Implemented
Set up Jenkins on an AWS EC2 instance.

Installed and configured Docker on the EC2 instance.

Integrated Jenkins with a GitHub repository.

Created a Jenkins Pipeline using a Jenkinsfile.

Implemented pipeline stages for checkout, testing, Docker image creation, and deployment.

Used Jenkins parameters for controlling application deployment.

Practiced using Jenkins environment variables and credentials securely.

Configured a GitHub Webhook to automatically trigger the Jenkins pipeline when code changes are pushed.

Built and deployed a containerized web application using Docker and Nginx.

Configured Docker port mapping to make the application accessible.

Key Concepts Learned

Jenkins Pipeline

Jenkinsfile

GitHub Webhooks

CI/CD

Docker Images and Containers

Dockerfile

Jenkins Parameters

Jenkins Environment Variables

Jenkins Credentials

Conditional Pipeline Stages

AWS EC2

Automated Application Deployment

Project Outcome
Successfully implemented an automated CI/CD workflow where a code change in GitHub triggers Jenkins and results in the application being rebuilt and deployed using Docker on AWS EC2.
