<h2>Docker quick start</h2>

Docker Repository file CentOS

```
[vagrant@dockertest ~]$ cat /etc/yum.repos.d/docker.repo 
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/7/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
```

Install Docker CentOS

```
[vagrant@dockertest ~]$ sudo yum install -y docker-engine
[vagrant@dockertest ~]$ sudo systemctl enable docker
[vagrant@dockertest ~]$ sudo systemctl start docker
```

Version/Add user to group for use socket

```
[vagrant@dockertest ~]$ docker --version
[vagrant@dockertest ~]$ usermod -a -G docker vagrant
```
List Docker images / Search Docker images / Run Docker Images

```
[vagrant@dockertest ~]$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              f7b3f317ec73        5 days ago          117MB
hello-world         latest              48b5124b2768        3 months ago        1.84kB
[vagrant@dockertest ~]$ docker search hello-world
NAME                                      DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
hello-world                               Hello World! (an example of minimal Docker...   293       [OK]       
tutum/hello-world                         Image to test docker deployments. Has Apac...   33                   [OK]
[vagrant@dockertest ~]$ docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
Digest: sha256:c5515758d4c5e1e838e9cd307f6c6a0d620b5e07e6f927b07d05f6d12a1ac8d7
Status: Image is up to date for hello-world:latest
[vagrant@dockertest ~]$ docker run hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/
 ```
