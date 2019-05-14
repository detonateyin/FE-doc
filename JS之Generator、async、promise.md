# JS之Generator、async、promise


1. Generator
    
    暂略

2. Promise

    暂略

3. Async

    参考了**flypie**于segmentfault发布的[《简单理解Generator自执行及async、await语法原理》](https://segmentfault.com/a/1190000008254704)一文总结为

    **Async就是一个Generator的语法糖，把Generator中的递归next重复代码用此语法糖代替，再把原来用thunk函数获取的返回值的获取权，以Promise的方式交出**

4. 使用Async的优点

    参考了**Fundebug**fundebug发布的译文[《Async/Await替代Promise的6个理由》](https://blog.fundebug.com/2017/04/04/nodejs-async-await/)一文总结为6个点

    1.简洁
    2.简单的捕捉错误并处理
    3.清晰地条件语句
    4.清晰中间值
    5.明确的错误栈信息抛出
    6.断点可以async而不能调试then