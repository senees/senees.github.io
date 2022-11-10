# Notes made while configuring VPS server based on CentOs 8

## Change root password

After logging-in for the first time to VPS as `root`, change the password:

```
# passwd
```

## Generate SSH keys

```
# mkdir ~/.ssh
# ssh-keygen -b 4098
```

## Copy keys from remote machine

```
# ssh-copy-id user@address
```

## Check the name and version of the operating system

```
# cat /etc/os-release
```

## Set locale

```
# localectl
# localectl list-locales
# localectl set-locale LANG=en_US.utf8
```

To remove the message `Failed to set locale, defaulting to C.UTF-8`, execute:

```
# dnf install langpacks-en glibc-all-langpacks -y
```

## Update system libraries

```
# yum update
```

## Install Docker

```
# dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
# dnf list docker-ce
# dnf install docker-ce --nobest -y
# systemctl start docker
# systemctl enable docker
```

Check installed version:

```
# docker --version
Docker version 20.10.7, build f0df350
```

## Install Docker Compose

Check the newest version of Docker Compose here: [https://github.com/docker/compose/releases](https://github.com/docker/compose/releases).

```
# curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

Sometimes it may be handy to use shorter name, like `dkc` to run Docker Compose, so create a symlink:

```
# ln -s /usr/local/bin/docker-compose /usr/bin/dkc
# chmod +x /usr/local/bin/docker-compose
```

Check installed version:

```
# dkc --version
docker-compose version 1.29.2, build 5becea4c
```

## Install nginx

```
# yum search nginx
# yum install nginx
# systemctl start nginx
# systemctl enable nginx
```

## Update firewall

```
# yum install firewalld
# systemctl start firewalld
# systemctl enable firewalld
# firewall-cmd --permanent --zone=public --add-service=https --add-service=http
# firewall-cmd --reload
```

## Install Certbot

```
# yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
# dnf install certbot python3-certbot-nginx
# certbot certonly --nginx
```

## Install Docker registry

```
# docker pull registry:2
# cd /opt
# mkdir registry
# cd registry
# mkdir auth
# mkdir certs
# mkdir data
# touch docker-compose.yml
```

Content of the `docker-compose.yml` file

```
version: '3'

services:

  registry:
    restart: always
    image: registry:2
    ports:
     - "port_number:5000"
    environment:
      REGISTRY_AUTH: htpasswd
      REGISTRY_AUTH_HTPASSWD_PATH: /auth/htpasswd
      REGISTRY_AUTH_HTPASSWD_REALM: Registry Realm
    volumes:
     - /opt/registry/data:/var/lib/registry
     - /opt/registry/certs:/certs
     - /opt/registry/auth:/auth
```

Create password file, change to `/opt/registry` directory:

```
# yum install httpd-tools
# docker run --entrypoint htpasswd httpd:2 -Bbn user password > auth/htpasswd ; history -d $(history 1)
```

Generate and copy certificates:

```
# certbot certonly --nginx
# cp /etc/letsencrypt/live/domain_name/fullchain.pem /opt/registry/certs/
# cp /etc/letsencrypt/live/domain_name/privkey.pem /opt/registry/certs/
```

Run the registry

```
# dkc up --no-start
# dkc start
# docker ps
```

Login to Docker registry

```
# docker login -u user_name domain_name
```
