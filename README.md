# beter4go

[English](https://github.com/huyinghuan/beter4go/edit/master/README_en.md)

写go的一些经验

## gzip

如果你的服务依赖其他的服务接口，在条件允许的时候，建议 依赖服务的接口  nginx层关闭gzip。

因为对应开启了gzip的接口，`ioutil.ReadAll`读取内容时，会调用gzip进行数据解压，在高qps的时候，会消耗比较高的io

如果不能修改nginx层，那么可以 通过设置header 来 `Accept-Encoding: 0` 来禁止nginx自动gzip。 【标准http服务器都支持。】
具体协议见： https://tools.ietf.org/html/rfc2616#section-14.2


## json

建议使用 github.com/json-iterator/go 代替原生 json 进行json序列化和反序列化, 在qps较高时，json的序列化和反序列化 比较耗io，如有可能，使用

[protocol buffer](https://developers.google.com/protocol-buffers/docs/gotutorial) 做服务间的数据传输协议，取代json

## 字符串拼接时

尽量使用 `strings.Join` 或 `strings.Builder` 减少内存重新分配 


