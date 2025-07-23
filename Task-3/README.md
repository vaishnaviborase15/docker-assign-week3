# Multi-Stage Docker Build Demo

This repository contains a simple Python application demonstrating the use of **multi-stage Docker builds** to create optimized Docker images.

---

## Project Structure

multi-stage-app/
├── app.py
├── requirements.txt
└── Dockerfile

yaml
Copy
Edit

- **app.py**: A simple Python script that prints a message.
- **requirements.txt**: Python dependencies (empty in this example).
- **Dockerfile**: Defines a multi-stage Docker build that installs dependencies in a builder stage and copies only the necessary files into the final lightweight image.

---

## Prerequisites

- [Docker](https://www.docker.com/get-started) installed on your machine.
- DockerHub account (optional, for pushing images).

---

## Usage

### 1. Build the Docker image

Run the following command in the root directory (`multi-stage-app`):

```bash
docker build -t <dockerhub-username>/multi-stage-demo:latest .
Example:

bash
Copy
Edit
docker build -t vaishnaviborase/multi-stage-demo:latest .
