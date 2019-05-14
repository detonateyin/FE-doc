# Vue系列之vuex.md

1. vuex是什么？解决了什么问题？
   - 状态管理器
   - 解决了组件之间共享同一状态

2. 核心概念
- State
  - Vuex 使用单一状态树——是的，用一个对象就包含了全部的应用层级状态，将所需要的数据写放这里，类似于data。
- Getter
  - 有时候我们需要从 store 中的 state 中派生出一些状态，使用Getter，类似于computed。
- Mutation
  - 更改 Vuex 的 store 中的状态的唯一方法，类似methods。
- Action
  - Action 提交的是 mutation，而不是直接变更状态，可以包含任意异步操作，这里主要是操作异步操作的，使用起来几乎和mutations方法一模一样,类似methods。
- Module
  - 当应用变得非常复杂时，store 对象就有可能变得相当臃肿。Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块

3. 单项数据流

    1. 用户访问 View
    2. View 发出用户的 Action
    3. Dispatcher 收到 Action，要求 Store 进行相应的更新
    4. Store 更新后，发出一个"change"事件
    5. View 收到"change"事件后，更新页面

4. vuex数据流？为什么要遵循这个数据流？假如在页面中直接修改state,而不是通过mutation 的commit方式修改，会怎么样？
   - 无法追踪更明确地追踪到状态的变化，不方便调试， vuex能够记录每一次state的变化记录，保存状态快照，实现时间漫游／回滚之类的操作。
   - strict模式下，无法直接修改state
5. vuex和redux区别

6. dispatch和commit的区别
   - dispatch 异步
   - commit 同步
7. 参考
  - [浅谈vuex](https://juejin.im/post/5a8fc988f265da4e914b73c6) 
