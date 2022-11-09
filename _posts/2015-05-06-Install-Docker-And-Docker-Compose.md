Source: [Install Docker Engine on Fedora](https://docs.docker.com/engine/install/fedora/)

```
$ sudo dnf -y install dnf-plugins-core
$ sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
$ sudo dnf install docker-ce docker-ce-cli containerd.io
$ sudo systemctl start docker
$ sudo systemctl enable docker
```

Add a user to **docker** group:

```
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
$ newgrp docker
```


