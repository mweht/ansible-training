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

