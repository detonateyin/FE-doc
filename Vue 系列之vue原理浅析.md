# Vue 系列之vue原理浅析

## 一、vue原理要素
- 生命周期
- Virtual Dom
- diff

### 1.1

### 1.2 Virtual Dom

#### 1.2.1snabbdom
是一个生成virtual-dom的库，再用diff来最小化更新网页，react的底层使用的同样的机制，vue2之后，在此库的基础上构建了一个fork版，也就是说vue2就是使用了snabbdom来的算法来构建virtual Dom，这里有篇介绍文章[走进snabbdom—Vue2背后的Virtual-DOM的机制](https://juejin.im/post/5a42119d5188256970783df1)，感兴趣的同学可以原味观看



### 1.3 diff
图解如下：
![virtualDomDiffWay](./source/virtualDomDiffWay.webP)


> 这是一张很经典的图，出自《React’s diff algorithm》，Vue的diff算法也同样，即仅在同级的vnode间做diff
——[深入Vue2.x的虚拟DOM diff原理](https://mp.weixin.qq.com/s/pd0Mshl-f0aJ8C-1Vc95Zw)

（插一句，webP是Google推出的图片肉眼无损的压缩算法格式，能带来更小的图片体积）

diff的高效在于指挥同层结构比较，而不是根据树比较

>[VirtualDOM与diff(Vue实现)](https://juejin.im/post/59bfbd736fb9a00a52065ec7#heading-6)

比较的过程：

1. 当检测到有数据变化的时候，就通知订阅者触发update（vnode）
2. update会去执行patch
3. patch第一步先是用diff算法比较
4. diff的比较先是比较两个vnode是否是同一个
5. 同一个vnode会执行pathVnode
6. pathVnode的规则是
    1. 如果新旧VNode都是静态的，同时它们的key相同（代表同一节点），并且新的VNode是clone或者是标记了once（标记v-once属性，只渲染一次），那么只需要替换elm以及componentInstance即可。
    2. 新老都有子节点，执行updateChildren
    3. 新有子节点，老没有，删除老的文本，添加新的节点
    4. 新无子节点，老有，删除子节点
    5. 新老都无子节点，更新文本
7. updateChildren的步骤
    1. oldStartVnode、oldEndVnode与newStartVnode、newEndVnode两两比较
    2. newStartVnode从哈希表中找相同Vnode，有则向前移动，无则创建
    3. 删除多余的
    4. 新增缺少的

最后的比较结果会映射更新到真实的DOM上，无论在哪个平台，vue都做了适配