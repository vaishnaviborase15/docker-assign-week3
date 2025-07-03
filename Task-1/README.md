# Docker Basics Task - Windows 10

This README documents a basic Docker usage session on a Windows 10 machine. The objective of this task was to verify Docker installation, pull and run containers, manage images and containers, and clean up unused resources.

---

##  Task Summary

### 🖥️ System Info
- **OS**: Microsoft Windows 10 (Build 22000.2538)
- **Docker Client Version**: 27.1.1
- **Docker Server (Engine) Version**: 27.1.1
- **Docker Desktop Version**: 4.33.1

---

## Steps Performed

### 1. **Verify Docker Installation**
```bash
docker version
```
- Verified client and server info.

### 2. **Pull Docker Images**
```bash
docker pull ubuntu
docker pull hello-world
```
- Pulled the latest `ubuntu` and `hello-world` images from Docker Hub.

### 3. **Run hello-world Container**
```bash
docker run hello-world
```
- Tested Docker installation. Output confirmed successful setup.

### 4. **List Running and All Containers**
```bash
docker ps
docker ps -a
```
- Verified `hello-world` and older `alpine` containers were present.

### 5. **List All Docker Images**
```bash
docker images
```
- Listed downloaded images (`ubuntu`, `alpine`, `mywebapp`, `hello-world`).

### 6. **Run Ubuntu Container Interactively**
```bash
docker run -it ubuntu /bin/bash
```
- Accessed bash shell inside the Ubuntu container.
- Exited using `exit`.

### 7. **Remove Specific Container**
```bash
docker rm <container_id>
```
- Removed `hello-world` container using container ID.

### 8. **Remove Specific Image**
```bash
docker rmi <image_id>
```
- Removed `hello-world` image using image ID.

### 9. **Prune Stopped Containers**
```bash
docker container prune
```
- Cleaned up all stopped containers and reclaimed space.

---

## Files and Images Used

| Name              | Type     | Notes                             |
|-------------------|----------|------------------------------------|
| `ubuntu`          | Image    | Base Linux image for CLI use       |
| `hello-world`     | Image    | Used for Docker installation test  |
| `alpine`          | Image    | Lightweight Linux image (earlier)  |
| `mywebapp`        | Image    | Custom image (pre-existing)        |
| `w2containerregistry.azurecr.io/mywebapp` | Image | Same image from private registry |

---

##  Conclusion

The Docker environment was successfully set up and tested. Images were pulled and containers were managed efficiently using standard Docker commands. Unused containers and images were cleaned up to maintain system hygiene.

---

##  References

- [Docker Docs - Get Started](https://docs.docker.com/get-started/)
- [Docker Hub](https://hub.docker.com/)
