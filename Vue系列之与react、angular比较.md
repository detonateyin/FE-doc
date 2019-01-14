# Vue系列之与react、angular比较



## 一、Vue与react的比较

### 1.1 相同点
- 都是用vitural Dom
- 都提供响应式和组件化的视图组件
- 都有丰富的生态库群

### 1.2 react对比分析
> [对比其他框架](https://cn.vuejs.org/v2/guide/comparison.html)

> [个人理解Vue和React区别监听数据变化的实现原理不同](https://juejin.im/post/5b8b56e3f265da434c1f5f76)

- 思想
    - react 
        - 不可变数据
        - 数据变化不可具体感知
        - 写组件即写函数
    - vue 
        - 可变数据
        - 数据变化可具体感知
        - 写组建是写封装函数的参数对象，最终是由vue帮助生成

- 优化
    - Vue 通过 getter/setter 以及一些函数的劫持，能精确知道数据变化，不需要特别的优化就能达到很好的性能
    - React 默认是通过比较引用的方式进行的，如果不优化（PureComponent/shouldComponentUpdate）可能导致大量不必要的VDOM的重新渲染
- JSX对比template
    - JSX
        -  适合更多的逻辑类
        -  更加灵活，拥有整套JS的控制流程
    - template
        -  适合更多的表现类
        -  领域特定语言DSL，用更少的代码做更多的事
        -  更加贴近HTML，转移门槛较低
        -  vue也可以使用JSX
-  CSS
    -  react 是 CSS-IN-JS
    -  vue是单文件样式

- 数据流不同
    - react强调数据不可变，单向流
    - vue可以使用v-modle双向数据流
- 高阶组件
  > [探索Vue高阶组件](https://juejin.im/entry/5a524420f265da3e2e6252c5)

    - react
        - 放弃mixin
        - HOC 容易
    - vue
        - mixin简单
        - HOC实现难度高