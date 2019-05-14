# Webpack系列之webpack面试题

// TODO 

1. 什么是webpack ,webpack 与grunt 或者gulp有什么区别?
   - webpack就是打包器，递归查询依赖，然后进行打包生成最终文件
   - 优点是
      - code-splitting（代码分割）
      - 模块化（AMD,ESM,CommonJs）
      - 全局分析，会分析全局项目下所有引入的模块

2. 什么是bundle，什么是chunk，什么是module?
      - bundle 是打包后生成的文件
      - chunk 是依赖分析后分割出的代码块
      - module 是单独的模块

3. 什么是loader，什么是plugin？

4. 如何可以自动生成webpack配置？
   - 使用webpack-cli/vue-cli/etc…脚手架工具

5. webpack-dev-server和http服务器如nginx有什么区别?
   - webpack-dev-server使用内存来存储webpack开发下的打包文件，并且可以使用模块热更新功能，比传统的http服务对开发更加简单高效

6. 什么是模块热更新 HMR?


## 优化

1. 什么是长缓存，在webopack中如何做到长缓存优化？
   - chunkhash

2. 什么是Tree-Shaking，CSS可以Tree-Shaking吗?
   - Tree-Shaking是指在打包中去除那些引入了，但是在代码中没有被用到的那些死代码，在webpack中Tree-Shaking是通过UglifyJSPlugin来Tree-Shaking Js，CSS使用Purify-CSS。

## Webpack工程化总结

实时编译
开发服务
自动优化

webpack工程化思想

- 一切皆为模块
- 急速调试和响应速度
- 优化应该自动完成