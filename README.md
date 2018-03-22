# setting
## install

```
yum remove docker docker-common docker-selinux docker-engine
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum makecache fast
yum list docker-ce.x86_64 --showduplicates | sort -r
# install latest version!
yum install docker-ce-17.09.1.ce-1.el7.centos

```

## proxy
https://qiita.com/jeffi7/items/3e40c59744b5801fd40a


# docker network
## create docker-Network

    $ docker build -t image01 -f Dockerfile.01_pg10 .
    $ docker network create --subnet=192.168.1.0/24 dnw01
    $ docker run -d --privileged --net=dnw01 --ip=192.168.1.100 --name contener01 image01 /sbin/init
    $ docker exec -it contener01 /bin/bash

## remove docker-Network

    $ docker network rm dnw01

## check ip address of contener

    $ docker network inspect dnw01


# about timezone
- --security-opt --cap-add SYS_ADMIN 等のオプションもあるがうまくいかず
- --privileged でrunして、root で# timedatectl set-timezone Asia/Tokyo を実行する

# tips
- 不要になったら、`$ docker stop contener01; docker rm contener01`


