# AWS DevOps Flask App Demo

This is a simple Flask web application deployed on an AWS EC2 Ubuntu instance and dockerized using Docker.

## Tech Stack

- Python 3
- Flask
- Docker
- AWS EC2 (Ubuntu)
- Git & GitHub

## What this project does

- Runs a basic Flask web app with a single route (`/`) that returns a simple message.
- Deployed on an AWS EC2 Ubuntu instance.
- Exposed on port `5000` and accessible using the EC2 instance’s public IP.
- Dockerized using a custom Dockerfile and run inside a Docker container.

## Files

- `app.py` – Flask application code
- `requirements.txt` – Python dependencies (Flask, gunicorn)
- `Dockerfile` – Docker configuration to build the image

## High-level deployment steps (what I did)

1. Launched an Ubuntu EC2 instance on AWS.
2. Configured Security Groups to allow:
   - SSH (port 22)
   - HTTP (port 80)
   - Custom TCP (port 5000)
3. Connected to the instance using EC2 Instance Connect.
4. Installed Python and created a virtual environment.
5. Created `app.py` and `requirements.txt`, and tested the app with `python app.py`.
6. Installed Docker (`docker.io`) on the EC2 instance.
7. Created a `Dockerfile`, built a Docker image, and ran the container:
   - `sudo docker build -t devops-flask-app .`
   - `sudo docker run -d -p 5000:5000 --name devops-flask-container devops-flask-app`
8. Accessed the app in the browser using:
   - `http://<EC2_PUBLIC_IP>:5000`

## Future improvements

- Add Nginx as a reverse proxy.
- Add CI/CD using GitHub Actions to auto-deploy on EC2.
- Add logging and monitoring (CloudWatch / Prometheus).
