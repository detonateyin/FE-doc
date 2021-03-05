# Webpack系列之代码拆分

> 参考[《webpack之代码拆分》](https://juejin.im/post/5a6d7eeef265da3e4d72f1f9)
> 
> 参考[《webpack 4.x 代码分割实践》](https://www.jianshu.com/p/3c93c0e724ba)

1. 代码拆分的必要性
   - 前端资源文件体积过大会极大的影响性能，特别是移动端
   - 按需加载，首屏用不到的资源，没有必要一开始就加载

2. 代码拆分的方式
    1. Entry Points: 多入口分开打包
    2. Prevent Duplication:去重，抽离公共模块和第三方库
        1. webpack4之前用的commonChunkPlugin
        2. webpack4y用的SplitChunks
    3. Dynamic Imports:动态加载 
        1. import()
        2. webpack 特定的 require.ensure
