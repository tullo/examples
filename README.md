# Micro 示例  [![Travis CI](https://travis-ci.org/micro/examples.svg?branch=master)](https://travis-ci.org/micro/examples) [![Go Report Card](https://goreportcard.com/badge/micro/examples)](https://goreportcard.com/report/github.com/micro/examples)

这里包含有micro大部分功能的示例，如果您有例子可以贡献，可以提交上来。

由于英文版的示例大多过于简单，中文版的某些示例可能会进行加强。

## 中文分支

由于默认分支是英文的，为了让大家方便使用中文分支的代码和文档，大家在下载本仓库后，需要切换分支

- 先检测中文分支是否存在

```bash
$ git branch
* cn-lang  # 如果有cn-lang则代表拉取的仓库中包含了中文分支
  master

# 如果当前不在cn-lang分支上，即cn-lang前没有*号，则使用下面的命令
$ git checkout cn-lang 
```

- 如果没有，则从远端分支中签出

```bash
$ git checkout origin/branch
```

## 内容

大部分例子都依赖下面三个示例

- [service](service) - 简单实现的micro服务端
- [greeter](greeter) - 包含有完整（客户端、服务端、web、api）功能的Greeter问候服务示例
- [booking](booking) - 端到端应用示例

### 其它示例

下例示例持续翻译中并进行适当演译

- [api](api) - [API](https://micro.mu/docs/api_cn.html)使用示例
- [booking](booking) - A booking.com demo application
- [broker](broker) - A example of using Broker for Publish and Subscribing.
- [client](client) - Usage of the Client package to call a service.
- [command](command) - An example of bot commands as micro services
- [config](config) - Using Go Config for dynamic config
- [event](event) - Using the API Gateway event handler
- [filter](filter) - Filter nodes of a service when requesting
- [flags](flags) - Using command line flags with a service
- [form](form) - How to parse a form behind the micro api
- [function](function) - Example of using Function programming model
- [getip](getip) - Get the local and remote ip from metadata
- [graceful](graceful) - Demonstrates graceful shutdown of a service
- [greeter](greeter) - A complete greeter example (includes python, ruby examples)
- [heartbeat](heartbeat) - Make services heartbeat with discovery for high availability
- [helloworld](helloworld) - Hello world using micro
- [metadata](metadata) - Extracting metadata from context of a request
- [mocking](mocking) - Demonstrate mocking helloworld service
- [noproto](noproto) - Use micro without protobuf or code generation, only go types
- [options](options) - Setting options in the go-micro framework
- [plugins](plugins) - How to use plugins
- [pubsub](pubsub) - Example of using pubsub at the client/server level
- [grpc](grpc) - 示例如何使用[go-grpc](https://github.com/micro/go-grpc)
- [redirect](redirect) - An example of how to http redirect using an API service
- [roundrobin](roundrobin) - A stateful client wrapper for true round robin of requests
- [secure](secure) - Demonstrates use of transport secure option for self signed certs
- [server](server) - Use of the Server package directly to server requests.
- [service](service) - Example of the top level Service in go-micro.
- [sharding](sharding) - An example of how to shard requests or use session affinity
- [shutdown](shutdown) - Demonstrates graceful shutdown via context cancellation
- [stream](stream) - An example of a streaming service and client
- [template](template) - Api, web and srv service templates generated with the 'micro new' command
- [waitgroup](waitgroup) - Demonstrates how to use a waitgroup with a service
- [wrapper](wrapper) - 包装器示例，本例中包含有一个使用日志包含器的示例

## 社区

Find contributions from the community via the [explorer](https://micro.mu/explore/)

- [go-shopping](https://github.com/autodidaddict/go-shopping) - A sample product with a suite of services
- [shippy](https://github.com/EwanValentine/shippy) - A multi app demo and tutorial
- [microhq](https://github.com/microhq) - A place for micro services

## 依赖

- [Service Discovery](#service-discovery) 服务发现
- [Protobuf](#protobuf) protobuf工具

## 服务发现

所有的服务都需要服务发现，默认使用组播（mDNS，multicast DNS），因为组播不需要任务配置或注册中心服务。

如果在多台主机上试验或者想做得有弹性一些，那就使用consul。

### Consul


### 安装

这是mac下的安装方法，其它平台请参考[consul](https://www.consul.io/)

```
# install
brew install consul

# run
consul agent -dev
```

启动时使用`--registry=consul`标记指令便会激活使用consul。

例如：

```bash
service --registry=consul
```

## Protobuf

Protobuf用来生成服务与客户端消息类型与方法存根的协议。

需要注意是，proto原型文件有改动需要重新编译。

### 安装

protoc对不同的操作系统有不同要求，请参考[protoc](https://github.com/google/protobuf)安装。

安装好后，因为我们要根据proto原型文件来生成对应golang版本源码文件，所以需要拉取protobuf的golang插件：

```shell
go get github.com/golang/protobuf/{proto,protoc-gen-go}
```

micro的protobuf插件，用来生成micro风格的client与server存根方法和结构。

```shell
go get github.com/micro/protoc-gen-micro
```

### 编译proto文件

```shell
protoc --proto_path=$GOPATH/src:. --micro_out=. --go_out=. path/to/proto
```

## 译者信息

[ShuXian](https://github.com/printfcoder/go-micro-examples-cn)