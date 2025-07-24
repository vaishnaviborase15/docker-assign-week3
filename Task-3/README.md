# Multi-Stage Docker Build Demo

This repository demonstrates how to use **multi-stage Docker builds** to create a lightweight and production-ready Python Docker image.

## Project Structure

```
multi-stage-app/
├── app.py               # Simple Python script to run
├── requirements.txt     # Python dependencies (empty in this demo)
└── Dockerfile           # Multi-stage Dockerfile
```

## Dockerfile Overview

This Dockerfile uses a multi-stage build to:

1. Use `python:3.11-slim` as the **build stage** to install dependencies.
2. Copy only the necessary artifacts into the **final stage** to reduce image size.

### Sample Dockerfile (used in this project)

```Dockerfile
# Stage 1 - Builder
FROM python:3.11-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt

# Stage 2 - Final
FROM python:3.11-slim AS final
WORKDIR /app
COPY --from=builder /usr/local/lib/python3.11 /usr/local/lib/python3.11
COPY app.py .

CMD ["python", "app.py"]
```

##  Build the Docker Image

```bash
docker build -t vaishnaviborase/multi-stage-demo:latest .
```

## Run the Docker Container

```bash
docker run --rm vaishnaviborase/multi-stage-demo:latest
```

### Output

```
Hello from a multi-stage Docker build!
```

## Docker Image Info

After building, you can verify the image:

```bash
docker images
```

Example:

```
REPOSITORY                          TAG       IMAGE ID       SIZE
vaishnaviborase/multi-stage-demo   latest    2393b63c44ee   221MB
```

## Notes

- Ensure you are in the correct directory (`multi-stage-app`) before running build commands.
- The warning `FromAsCasing` can be safely ignored for this demo. It's best practice to use consistent casing for Dockerfile keywords like `FROM` and `AS`.

## Author

**Vaishnavi Borase**

>  *This demo is part of my Docker learning journey and shows how to reduce Docker image sizes using multi-stage builds.*
