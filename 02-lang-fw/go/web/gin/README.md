# go web

> gin-web

## 资源

> [gin](https://github.com/gin-gonic/gin)
>
> [Go语言WEB框架(Gin)详解](http://c.biancheng.net/view/5574.html)
>
>   - [案例项目 - tmm](https://github.com/ffhelicopter/tmm)
>

## 简介

在 Go语言开发的 Web 框架中，有两款著名 Web 框架分别是 Martini 和 Gin，两款 Web 框架相比较的话，Gin 自己说它比 Martini 要强很多。Gin 是 Go语言写的一个 web 框架，它具有运行速度快，分组的路由器，良好的崩溃捕获和错误处理，非常好的支持中间件和 json。

golang开发环境搭建完成，使用go module之后不用考虑gopath的配置，可以在电脑上任意一个目录创建一个go项目，而不是只能在$gopath/src/下，多个项目也不会互相影响，go的文件go.mod和go.sum也一起提交到git上，多人开发新增了模块只需要更新该文件即可。


### gin

gin 的功能不只是简单输出 Json 数据。它是一个轻量级的 WEB 框架，支持 RestFull 风格 API，支持 GET，POST，PUT，PATCH，DELETE，OPTIONS 等 http 方法，支持文件上传，分组路由，Multipart/Urlencoded FORM，以及支持 JsonP，参数处理等等功能，这些都和 WEB 紧密相关，通过提供这些功能，使开发人员更方便地处理 WEB 业务。

$> go get -u github.com/gin-gonic/gin  # 安装使用

> 使用案例

```go
// 1. Default返回一个默认的路由引擎
r := gin.Default()
// 2. 设置 GET 请求
r.GET("/ping", func(c *gin.Context) {
    //输出json结果给调用方
    c.JSON(200, gin.H{
        "message": "pong",
    })
})
// 3. listen and serve on 0.0.0.0:8080; curl http://localhost:8080/ping
r.Run()
```

### 配置步骤

1. 下载安装 golang

```log
$> go version

go version go1.17.6 windows/amd64
```

2. 初始化项目

$> mkdir gin-web && cd gin-web

$> go mod init gin-web

$> go get -u github.com/gin-gonic/gin # 下载安装gin框架

$> touch main.go

```go main.go
package main

import "github.com/gin-gonic/gin"

func main() {
 r := gin.Default()
 r.GET("/ping", func(c *gin.Context) {
  c.JSON(200, gin.H{
   "message": "pong",
  })
 })
 r.Run() // listen and serve on 0.0.0.0:8080
}
```

$> go run main.go

