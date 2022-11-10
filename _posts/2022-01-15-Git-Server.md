# GIT server

Install git

```
# yum install git
```

Create user

```
# useradd -r -m -U -d /home/git -s /bin/bash git
```

Switch to user **git**

```
# sudo su - git
```

Create a directory for SSH keys

```
# mkdir -p ~/.ssh && chmod 0700 ~/.ssh
```

Create a file for storing authorized SSH keys

```
# touch ~/.ssh/authorized_keys && chmod 0600 ~/.ssh/authorized_keys
```

Disable shell for `git` user:

```
# cat /etc/shells   
# which git-shell   
# sudo -e /etc/shells
```

```
# sudo chsh git -s $(which git-shell)
```

Create an empty repository, must be created under /home/git

```
# git init --bare your_repository_name.git
```

Migrate the whole repository from existing repository (e.g. on bitbucket):

```
$ git clone --bare git@bitbucket.org:company_name/your_repository_name.git
$ cd your_repository_name.git
$ git push --mirror git@your_domain:~/your_repository_name.git
```

Clone from repository

```
git clone git@your_domain:~/your_repository_name.git
```

## References:

- [https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server](https://git-scm.com/book/en/v2/Git-on-the-Server-Setting-Up-the-Server)
