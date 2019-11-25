# How to Install Go 1.13 on Ubuntu.

Go is an opensource programing language developed by google. It's very popular and many companies using their application in go. It has robust set of library and tools. Many applications such as Docker and Kubernetes are written in Go. In this tutorial i will help you to install Go version `1.13.4` in Ubuntu 18.04.


### Remove the existing golang
You have to remove existing golang from your machine.
```
sudo apt-get purge golang*
```

### Download Go.
Download the latest version of the Go from it's official website. Click here to more.

```
https://dl.google.com/go/go1.13.4.linux-amd64.tar.gz
```

### Extract it in /usr/local using the command below, You have to replace the filename with the actual filename based on the version you have downloaded.

tar -C /usr/local -xzf go1.13.4.linux-amd64.tar.gz


### Create .go directory in home.
```
mkdir /go
```

### Set up the environment variables.

```
GOROOT=/usr/local/go
GOPATH=~/go
PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

### Update the go command

sudo update-alternatives --install "/usr/bin/go" "go" "/usr/local/go/bin/go" 0
sudo update-alternatives --set go /usr/local/go/bin/go

### Check the Go version.
```
go version
---go version go1.13.4 linux/amd64---
```


### Verify the variables settings.

```
go env
```
```
GOARCH="amd64"
GOBIN=""
GOCACHE="/root/.cache/go-build"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="linux"
GOOS="linux"
GOPATH="/root/go"
GOPROXY=""
GORACE=""
GOROOT="/usr/local/go"
GOTMPDIR=""
GOTOOLDIR="/usr/local/go/pkg/tool/linux_amd64"
GCCGO="gccgo"
CC="gcc"
CXX="g++"
CGO_ENABLED="1"
GOMOD=""
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="-fPIC -m64 -pthread -fmessage-length=0 -fdebug-prefix-map=/tmp/go-build957428155=/tmp/go-build -gno-record-gcc-switches"
```
