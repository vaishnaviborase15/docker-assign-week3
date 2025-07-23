# Dockerized Python Application

This project demonstrates how to containerize a simple Python application using Docker. It includes the source code (`app.py`) and a `Dockerfile` for building a lightweight, standalone image.

---

##  Project Structure

```
mydockerapp/
│
├── app.py            # Simple Python script
└── Dockerfile        # Docker build instructions
```

---

##  Prerequisites

- Docker installed on your system (Windows, Linux, or Mac)  
   [Install Docker](https://docs.docker.com/get-docker/)

---

##  Getting Started

### 1. Clone or navigate to the project directory

```bash
cd D:\W4-T2\mydockerapp
```

### 2. View the application code

**app.py**

```python
print("Hello from my Docker image!")
```

---

## Build the Docker Image

From the project root directory (`mydockerapp`), run:

```bash
docker build -t mypythonapp:1.0 .
```

> This command builds a Docker image named `mypythonapp` with the tag `1.0`.

---

## Run the Docker Container

Run the container to see the output:

```bash
docker run mypythonapp:1.0
```

Or run and remove the container after execution:

```bash
docker run --rm mypythonapp:1.0
```

---

##  Open an Interactive Shell Inside the Container

```bash
docker run -it mypythonapp:1.0 /bin/bash
```

Once inside the container, you can run:

```bash
ls           # To list files
python app.py  # To manually run the script
exit         # To exit the container
```

---

## Cleanup (Optional)

To remove the image:

```bash
docker rmi mypythonapp:1.0
```

---

## Image Info

- **Base Image**: `python:3.10-slim`
- **Image Size**: ~192 MB
- **Purpose**: Educational use of Docker with Python

---

##  References

- [Docker Documentation](https://docs.docker.com/)
- [Python Docker Hub Image](https://hub.docker.com/_/python)

---

## Author

**Vaishnavi Borase**  
B.Tech CSE (Data Science), R. C. Patel Institute of Technology  
Email: *[vaishnaviborse.clg@gmail.com]*  
GitHub: [github.com/Vaishnaviborse15](https://github.com/Vaishnaviborse15)

---

## License

This project is for educational and demonstration purposes only. Feel free to modify and reuse.
