# beter4go
写go的一些经验


- 如果你的服务依赖其他的服务接口，在条件允许的时候，建议 依赖服务的接口  nginx层关闭gzip， 因为对应开启了gzip的接口，`ioutil.ReadAll`读取内容时，会调用gzip进行数据解压，在高qps的时候，会消耗比较高的io
- 多字符串拼接时，尽量使用 `strings.Join` 或 `strings.Builder` 减少内存重新分配 
