# JS之模块化

1. 模块化的方式
   - CommonJS 服务端 同步加载
   - AMD/CMD/UMD 客户端 异步加载
      - AMD 提前定义依赖
      - CMD 就近定义依赖
      - UMD 通用解决方案，三个步奏：判断是否支持 AMD，判断是否支持 CommonJS，如果都没有 使用全局变量
   - ESM 客户端 异步加载（即export / import）
2.