# Webpack系列之打包优化策略

> 本文由拜读了 **wenli** 在掘金写的一篇文章[《webpack4.0打包优化策略》（一）、（二）、（三）](https://juejin.im/post/5abbc2ca5188257ddb0fae9b)而总结，推荐原味阅读

1. 优化loader配置
    1. 缩小文件匹配范围(include/exclude)
    2. 缓存loader的执行结果(cacheDirectory)
2. resolve优化配置
    1. 优化模块查找路径，不用递归向上查找，而是写明node_modules的全路径
    2. 