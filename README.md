# aws-docker-containerization-lab
Hands-on Docker deployment on AWS EC2, including custom images, Docker Compose, networking, persistent volumes, reverse proxying, and service health checks.

# AWS Docker & Containerization Lab

## Overview

Deployed and managed containerized web applications on AWS EC2 using Docker Engine and Docker Compose.

Built custom Docker images, configured container networking and persistent storage, implemented an Nginx reverse proxy, and monitored application health.

## Technologies

- AWS EC2 and Ubuntu Linux
- Docker Engine and Docker CLI
- Docker Compose
- Nginx
- Python HTTP Server
- Docker Bridge Networking
- Docker Volumes
- HTTP, Linux, and curl

## Architecture

Client → Nginx Container → Docker Bridge Network → Python HTTP Service

Both services run on an AWS EC2 instance. The Nginx service listens on EC2 localhost port 8082 and forwards `/api/` requests to the Python service on Docker's internal network.

## Implementation

1. Installed Docker Engine on Ubuntu EC2.
2. Downloaded and launched an official Nginx Docker image.
3. Built a custom Nginx image using a Dockerfile.
4. Deployed and updated a containerized HTML website using versioned images.
5. Used Docker CLI tools to inspect containers, logs, and resource utilization.
6. Configured an `unless-stopped` restart policy.
7. Created a Docker volume and verified data persistence across temporary containers.
8. Deployed Nginx and Python HTTP services using Docker Compose.
9. Verified communication between containers through Docker's internal DNS.
10. Configured Nginx as a reverse proxy for the Python service.
11. Simulated an API outage and diagnosed the resulting HTTP 502 error.
12. Restored the API and verified successful HTTP 200 responses.
13. Configured an HTTP-based health check for the API container.

## Troubleshooting

### Docker Port Conflict

Encountered an error when attempting to publish two containers on the same host port.

Used `docker ps -a` and Linux networking commands to identify the conflict.

### HTTP 502 Bad Gateway

Stopped the Python backend and observed Nginx returning HTTP 502.

Inspected service status and logs, restarted the API, and verified recovery with HTTP 200.

### Container Health Monitoring

Implemented a Docker health check to verify that the Python service responds to HTTP requests.

## Key Concepts Learned

- Docker images versus running containers
- Container lifecycle and immutable deployments
- Host ports versus container ports
- Internal Docker networking and DNS
- Persistent volumes
- Reverse proxies and backend service communication
- Container monitoring and health checks

## Future Improvements

- Automate container image builds using GitHub Actions.
- Push custom images to Amazon ECR.
- Deploy containers using Amazon ECS.
- Implement centralized logging and monitoring.
- Manage AWS infrastructure using Terraform.

## Project Status

Completed - Hands-on Docker and Docker Compose deployment on AWS EC2.
