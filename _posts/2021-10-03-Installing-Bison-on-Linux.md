Head to GNU/Bison web page: https://www.gnu.org/software/bison/

Select the download source, let say GNU/FTP: http://ftp.gnu.org/gnu/bison/

Download the newest version (it was 3.8.2 at the time of writing this post):

```
$ wget http://ftp.gnu.org/gnu/bison/bison-3.8.2.tar.gz
```

Unpack sources:

```
$ tar -xzf bison-3.8.2.tar.gz
$ cd bison-3.8.2
```

Before proceeding check if **m4** is already installed, if not:

```
$ sudo yum install m4
```

Configure, build and install Bison from sources:

```
$ ./configure
$ make
$ sudo make install
```

Check the installed version:

```
$  bison -V
bison (GNU Bison) 3.8.2
```

**Done.**
