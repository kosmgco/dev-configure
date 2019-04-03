# Node.js 开发环境配置

## Android 

```
pkg install nodejs
```

## Arch Linux

```
pacman -S nodejs npm
```

## Debian and Ubuntu based Linux distributions, Enterprise Linux/Fedora and Snap packages

[Nodejs 官方发行版](https://github.com/nodesource/distributions/blob/master/README.md) 

## FreeBSD

```
pkg install node
```

或者

```
cd /usr/ports/www/node && make install
```

## Gentoo

```
emerge nodejs
```

## NetBSD

```
cd /usr/pkgsrc/lang/nodejs && make install
```

或者

```
pkgin -y install nodejs
```

## nvm

Node 版本管理工具是一个用来管理多版本 Node 的 bash 脚本，可以安装，卸载，切换版本等等。可以使用这个[脚本](https://github.com/creationix/nvm#install-script)来安装。

在 Unix/OS X 中

```
$ env VERSION=`python tools/getnodeversion.py` make install DESTDIR=`nvm_version_path v$VERSION` PREFIX=""
```

```
$ nvm use 8
```

卸载

```
$ nvm uninstall 8
```

## OpenBSD

```
pkg_add node
```

## macOS

```
curl "https://nodejs.org/dist/latest/node-${VERSION:-$(wget -qO- https://nodejs.org/dist/latest/ | sed -nE 's|.*>node-(.*)\.pkg</a>.*|\1|p')}.pkg" > "$HOME/Downloads/node-latest.pkg" && sudo installer -store -pkg "$HOME/Downloads/node-latest.pkg" -target "/"
```

使用HomeBrew

```
brew install node
```

使用 MacPorts

```
port install nodejs<major version>

# Example
port install nodejs7
```

使用pkgsrc

```
pkgin -y install nodejs
```

或者

```
cd pkgsrc/lang/nodejs && bmake install
```

## REF

[Installing Node.js via package manager | Node.js](https://nodejs.org/en/download/package-manager/)
