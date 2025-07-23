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
2. Run the Docker container locally
bash
Copy
Edit
docker run --rm vaishnaviborase/multi-stage-demo:latest
Expected output:

css
Copy
Edit
Hello from a multi-stage Docker build!
3. (Optional) Push the image to DockerHub
Login to DockerHub:

bash
Copy
Edit
docker login
Push the image:

bash
Copy
Edit
docker push vaishnaviborase/multi-stage-demo:latest
Dockerfile Explanation
This Dockerfile uses multi-stage builds to optimize image size:

Builder stage (python:3.11-slim): Installs all Python dependencies.

Final stage (python:3.11-slim): Copies only the Python runtime libraries and the application code from the builder stage, resulting in a smaller final image.

Notes
The current requirements.txt file is empty, but you can add your Python dependencies as needed.

Make sure to replace <dockerhub-username> with your actual DockerHub username in all commands.

Author
Vaishnavi Borase

License
This project is licensed under the MIT License.
