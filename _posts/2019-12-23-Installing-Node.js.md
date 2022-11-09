Installation of Node.js via packege manager is decsribed [here](https://nodejs.org/en/download/package-manager/).

Example of the installation on Fedora i described below.

Check the available list of Node.js streams:

```
$ sudo dnf module list nodejs
```

To install for example stream 16:

```
$ sudo dnf module install nodejs:16/default
```

Check installed versions:

```
$ npm -v
```

```
$ node -v
```