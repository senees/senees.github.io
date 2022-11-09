Checking outdated dependencies:

```
$ npm outdated
```

Example outout:

```
Package              Current  Wanted  Latest  Location                          Depended by
copy-webpack-plugin   10.2.4  10.2.4  11.0.0  node_modules/copy-webpack-plugin  app
css-loader             6.6.0   6.7.1   6.7.1  node_modules/css-loader           app
html-loader            3.1.0   3.1.2   4.2.0  node_modules/html-loader          app
ts-loader              9.2.6   9.4.1   9.4.1  node_modules/ts-loader            app
typescript             4.5.5   4.8.4   4.8.4  node_modules/typescript           app
uuid                   8.3.2   8.3.2   9.0.0  node_modules/uuid                 app
webpack               5.69.1  5.75.0  5.75.0  node_modules/webpack              app
webpack-cli            4.9.2  4.10.0  4.10.0  node_modules/webpack-cli          app
webpack-dev-server     4.7.4  4.11.1  4.11.1  node_modules/webpack-dev-server   app
```

For an advanced and customizable upgrading experience use `npm-check-updates`:

```
$ sudo npm install -g npm-check-updates
```

Chceck dependencies:

```
$ ncu
```

Example output:

```
[====================] 15/15 100%

 copy-webpack-plugin  ^10.2.4  →  ^11.0.0
 css-loader            ^6.6.0  →   ^6.7.1
 html-loader           ^3.1.0  →   ^4.2.0
 ts-loader             ^9.2.6  →   ^9.4.1
 typescript            ^4.5.5  →   ^4.8.4
 uuid                  ^8.3.2  →   ^9.0.0
 webpack              ^5.69.1  →  ^5.75.0
 webpack-cli           ^4.9.2  →  ^4.10.0
 webpack-dev-server    ^4.7.4  →  ^4.11.1
```

Upgrade and install new versions of dependencies:

```
$ ncu -u
$ npm install
```
