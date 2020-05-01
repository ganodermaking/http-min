# http-min
基于docker scratch最小的http服务器

#### 编译可执行文件
scratch 是一个特殊的镜像，它是一个虚拟镜像，也就是一个空白镜像；利用Golang的静态化编译无依赖性，可以大幅度减少编译时间和镜像大小。
```shell
CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o http-min .
```
> GOOS=linux 是将交叉编译的目标设置为Linux，这样你在Mac或者Win下也不会出现问题。 -installsuffix cgo 是为了在静态编译中导入net

#### 构建镜像
```shell
docker build -t scratch/http-min:latest .
```

#### 运行容器
```shell
docker run -it --name http-min -p 1234:1234 -d scratch/http-min:latest
```
