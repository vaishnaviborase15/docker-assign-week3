# Task-1 : Introduction to containerization and Docker fundamentals, Basic Commands

Microsoft Windows [Version 10.0.22000.2538]
(c) Microsoft Corporation. All rights reserved.

C:\Users\admin>docker version
Client:
 Version:           27.1.1
 API version:       1.46
 Go version:        go1.21.12
 Git commit:        6312585
 Built:             Tue Jul 23 19:57:57 2024
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.33.1 (161083)
 Engine:
  Version:          27.1.1
  API version:      1.46 (minimum version 1.24)
  Go version:       go1.21.12
  Git commit:       cc13f95
  Built:            Tue Jul 23 19:57:19 2024
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.7.19
  GitCommit:        2bf793ef6dc9a18e00cb12efb64355c2c9d5eb41
 runc:
  Version:          1.7.19
  GitCommit:        v1.1.13-0-g58aa920
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

C:\Users\admin>docker pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
d9d352c11bbd: Pull complete
Digest: sha256:b59d21599a2b151e23eea5f6602f4af4d7d31c4e236d22bf0b62b86d2e386b8f
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview ubuntu


C:\Users\admin>docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
e6590344b1a5: Pull complete
Digest: sha256:940c619fbd418f9b2b1b63e25d8861f9cc1b46e3fc8b018ccfe8b78f19b8cc4f
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview hello-world


C:\Users\admin>docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/


C:\Users\admin>docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

C:\Users\admin>docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
e596219126f0   hello-world   "/hello"   32 seconds ago   Exited (0) 31 seconds ago             inspiring_tesla
a9168186806f   alpine        "sh"       3 days ago       Exited (255) 44 hours ago             container2
8a1269d38748   alpine        "sh"       3 days ago       Exited (255) 44 hours ago             container1

C:\Users\admin>docker images
REPOSITORY                                TAG       IMAGE ID       CREATED        SIZE
mywebapp                                  v1        66f6331891a3   2 weeks ago    48.2MB
w2containerregistry.azurecr.io/mywebapp   v1        66f6331891a3   2 weeks ago    48.2MB
alpine                                    latest    cea2ff433c61   4 weeks ago    8.31MB
ubuntu                                    latest    bf16bdcff9c9   4 weeks ago    78.1MB
hello-world                               latest    74cc54e27dc4   5 months ago   10.1kB



C:\Users\admin>docker run -it ubuntu /bin/bash
root@d72456140a53:/# exit
exit



C:\Users\admin>docker rm e596219126f0e17aefea4d04369aa8dbed37c8dd24455a1ff760a5892ce8543d
e596219126f0e17aefea4d04369aa8dbed37c8dd24455a1ff760a5892ce8543d

C:\Users\admin>docker rmi 74cc54e27dc41bb10dc4b2226072d469509f2f22f1a3ce74f4a59661a1d44602
Untagged: hello-world:latest
Untagged: hello-world@sha256:940c619fbd418f9b2b1b63e25d8861f9cc1b46e3fc8b018ccfe8b78f19b8cc4f
Deleted: sha256:74cc54e27dc41bb10dc4b2226072d469509f2f22f1a3ce74f4a59661a1d44602
Deleted: sha256:63a41026379f4391a306242eb0b9f26dc3550d863b7fdbb97d899f6eb89efe72

C:\Users\admin>docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
d72456140a533cc2ad9d7ca16a353d1761083a9abb844fa8c82847157615348d
a9168186806fcb82d4b8786095036aeef47218b42583feacd0d735c4b7a60d09
8a1269d387489c83324c6c5aea83ae99615d20e5adaaa58771c30aa5e28920ca

Total reclaimed space: 26B

C:\Users\admin>
