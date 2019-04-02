# Golang 开发环境配置

[TOC]

## Linux，MacOS，FreeBSD tar包安装

[下载压缩包](https://golang.org/dl/) 然后解压到 `/usr/local`，在 `/usr/local/go` 创建一个树形目录。例如：

```
tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

为你的安装选择一个合适的安装包。例如，如果你要在 64 位 x86 Linux 计算机上安装 Go1.2.1，你应该选择的压缩包是 `go1.2.1.linux-amd64.tar.gz`。

（这些命令需要在 root 权限下运行或者使用 `sudo`）

添加 `/usr/local/go/bin` 到你的 `PATH` 环境变量，将以下内容添加到 `/etc/profile` 或者 `$HOME/.profile`。

```
export PATH=$PATH:/usr/local/go/bin
```

** 如果是修改 `profile文件`，那么可能直到你下次登录你的电脑之前都不会更新，为了让以上命令立刻生效，可以直接在命令行运行，也可以执行 `source $HOME/.profile`。 **

## Mac OS X 包安装器

[下载打包好的文件](https://golang.org/dl/)，打开后按照提示进行安装 Go 工具。这将会将 Go 安装在 `/usr/local/go`。

这将会将你的 `/usr/local/go/bin` 目录放到 `PATH` 环境变量中，你需要重启任何已经开启的终端窗口来使之生效。

## Windows

Go 项目组为 Windows 用户提供了 2 种方式（除了用源码安装）来安装 Go 环境：

### 1. MSI 安装器

将会自动配置环境

打开[MSI文件](https://golang.org/dl/)，然后跟随提示来安装 Go 工具。默认地，安装器将会把 Go 安装在 `C:\Go`。

安装器将会把 `C:\Go\bin` 目录添加到 `PATH` 环境变量中。你可能需要重启任何已经打开的命令行重启来让设置生效。

### 2. Zip 压缩包

需要自己设置环境变量

[下载zip压缩包](https://golang.org/dl/)然后解压到你选择的目录（建议 `c:\Go`）。

添加你的 `Go root` 的子目录 `bin` （例如：`c:\Go\bin`）到你的环境变量。

### 在 Windows 中设置环境变量

在 Windows 下，设置环境变量需要在 系统控制面板 下的 高级 选项卡中点击 环境变量 按钮。一些版本的 Windows 系统在 系统控制面板 中的 高级系统设置 。

## 测试你的安装结果

检查 Go 环境是否安装完成，通过创建一个工作空间，并编译一个小程序。如下：

创建你的 [工作空间](https://golang.org/doc/code.html#Workspaces)，`$HOME/go`。（如果你需要使用一个不同的目录，你需要[设置你的GOPATH环境变量](https://golang.org/wiki/SettingGOPATH)）。

然后，在你的工作空间中创建一个目录 `src/hello` ，然后在这个目录下创建一个 `hello.go` 文件。 内容如下：

```
package main

import "fmt"

func main () {
    fmt.Println("hello world\n")
}
```

然后使用 Go 工具构建：

```
$ cd $HOME/go/src/hello
$ go build
```

这个命令将会在你的源代码旁边构建一个叫 `hello` 的可执行文件。执行将会看到欢迎语。

```
$ ./hello
hello world
```

如果你看到 `hello world`，就表明你的安装是生效的。

你可以运行 `go install` 来将二进制文件安装到你的工作空间的 `bin` 目录下，使用 `go clean -i` 来移除已安装的二进制文件。

在急于写 Go 代码之前，请阅读 [如何编写 Go 代码](https://golang.org/doc/code.html) 文档，该文档描述了一些关于编写 Go 代码的基本概念。

## 安装额外的Go版本

在同一台机器上安装多版本 Go 工具时是非常有用的。例如：为了确保一个包的测试用例在多版本下均通过。一旦你安装了一个 Go 的版本，你就可以使用以下命令安装另外的版本（比如1.10.7）。

```
$ go get golang.org/dl/go1.10.7
$ go1.10.7 download
```

新下载的 Go 版本可以根据如下命令来使用

```
$ go1.10.7 version
go version go1.10.7 linux/amd64
```

此方法对 [下载页面](https://godoc.org/golang.org/dl#pkg-subdirectories) 中列出的所有的 Go 版本均可用。

## 卸载 Go

要从你的机器中卸载 Go，直接删除 `go` 目录即可。在 Linux，MacOS，FreeBSD 中通常在`/usr/local/go`，Windows 则在 `c:\Go`。

你需要移除环境变量中的 Go bin 目录，Linux，MacOS，FreeBSD 中编辑 `/etc/profile` 或者 `$HOME/.profile` 文件。如果你使用 MacOS 安装器的方式安装的 Go，则需要移除 `/etc/paths.d/go` 文件。Windows 用户需要阅读 `在 Windows 中设置环境变量` 一节。

## REF

[Getting Started - The Go Programming Language](https://golang.org/doc/install)
