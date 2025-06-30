# Task: Docker installation and basic container operations, Build an image from Dockerfile

Container Operations
```
C:\Users\admin>docker run -it ubuntu /bin/bash
root@bf9c0b9c4762:/# exit
exit

C:\Users\admin>docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

C:\Users\admin>docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                      PORTS     NAMES
bf9c0b9c4762   ubuntu    "/bin/bash"   31 seconds ago   Exited (0) 11 seconds ago             eager_sammet

C:\Users\admin>docker stop bf9c0b9c4762f8be467ff12742311aca434702578372d2af67e2f625f9642fc7
bf9c0b9c4762f8be467ff12742311aca434702578372d2af67e2f625f9642fc7

C:\Users\admin>docker rm bf9c0b9c4762f8be467ff12742311aca434702578372d2af67e2f625f9642fc7
bf9c0b9c4762f8be467ff12742311aca434702578372d2af67e2f625f9642fc7


```
Creating the image
```
C:\Users\admin>cd desktop

C:\Users\admin\Desktop>cd doctestapp

C:\Users\admin\Desktop\doctestapp>docker build -t demopyimage .
[+] Building 89.6s (10/10) FINISHED                                                                                                                    docker:desktop-linux
 => [internal] load build definition from dockerfile                                                                                                                   0.1s
 => => transferring dockerfile: 169B                                                                                                                                   0.0s
 => [internal] load metadata for docker.io/library/python:3.9-slim                                                                                                     5.4s
 => [auth] library/python:pull token for registry-1.docker.io                                                                                                          0.0s
 => [internal] load .dockerignore                                                                                                                                      0.0s
 => => transferring context: 2B                                                                                                                                        0.0s
 => [1/4] FROM docker.io/library/python:3.9-slim@sha256:a40cf9eba2c3ed9226afa9ace504f07ad30fe831343bb1c69f7a6707aadb7c21                                              74.6s
 => => resolve docker.io/library/python:3.9-slim@sha256:a40cf9eba2c3ed9226afa9ace504f07ad30fe831343bb1c69f7a6707aadb7c21                                               0.1s
 => => sha256:78cf9008e07b75b10639f04d47f64ee5a0e65ae794e704123462a0aea0bd4e68 1.75kB / 1.75kB                                                                         0.0s
 => => sha256:07f17bb34a51732d91685dea8f43319a3799414e49e54b6b25fc8985debe91b6 5.29kB / 5.29kB                                                                         0.0s
 => => sha256:dad67da3f26bce15939543965e09c4059533b025f707aad72ed3d3f3a09c66f8 28.23MB / 28.23MB                                                                      67.0s
 => => sha256:a40cf9eba2c3ed9226afa9ace504f07ad30fe831343bb1c69f7a6707aadb7c21 10.41kB / 10.41kB                                                                       0.0s
 => => sha256:20a97c0d8fc11f8337ff080be3f192c7211a0b7d1e6b886d6d2cff6674761652 3.51MB / 3.51MB                                                                        10.4s
 => => sha256:cd1e1b7e12d38cac4095e7ea4f161334542f130d381d6ef2013fa1ac01b4b6b0 14.94MB / 14.94MB                                                                      53.5s
 => => sha256:ea13ebdb5390b4e3fa5651d1daf14e6756a134f9a168fbedde44f02b1cee5fa8 250B / 250B                                                                            10.9s
 => => extracting sha256:dad67da3f26bce15939543965e09c4059533b025f707aad72ed3d3f3a09c66f8                                                                              3.9s
 => => extracting sha256:20a97c0d8fc11f8337ff080be3f192c7211a0b7d1e6b886d6d2cff6674761652                                                                              0.4s
 => => extracting sha256:cd1e1b7e12d38cac4095e7ea4f161334542f130d381d6ef2013fa1ac01b4b6b0                                                                              2.2s
 => => extracting sha256:ea13ebdb5390b4e3fa5651d1daf14e6756a134f9a168fbedde44f02b1cee5fa8                                                                              0.0s
 => [internal] load build context                                                                                                                                      0.2s
 => => transferring context: 180B                                                                                                                                      0.1s
 => [2/4] WORKDIR /doctestapp                                                                                                                                          0.7s
 => [3/4] COPY hello.py ./                                                                                                                                             0.1s
 => [4/4] RUN pip install --no-cache-dir requests                                                                                                                      8.1s
 => exporting to image                                                                                                                                                 0.3s
 => => exporting layers                                                                                                                                                0.3s
 => => writing image sha256:58a470b4bf2932f961d9598bc136c01daa3746ebf72bd0a737241924e423b0fa                                                                           0.0s
 => => naming to docker.io/library/demopyimage                                                                                                                         0.0s

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview


C:\Users\admin\Desktop\doctestapp>docker run demopyimage
Hello from team
GitHub API status: 200

C:\Users\admin\Desktop\doctestapp>
