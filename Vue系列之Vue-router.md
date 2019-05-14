# Vue系列之Vue-router原理简析

> 今日阅读了一片关于vue-router的浅析讲解，觉得不错，特此总结，有兴趣的同学推荐原味阅读，[《浅谈vue-router原理》](https://www.jianshu.com/p/4295aec31302)

1. vue-router原理
   - 都是通过修改浏览器历史记录栈来完成路由切换
      - hash(默认)
      - history
      - abstract

2. hash
   - hash 即锚点(#)
   - new HashHistory()
   - hashHistory.push()
   - hashHistory.replace()

3. history
   - new HtmlHistory()
   - htmlHistory.pushState()
   - htmlHistory.replaceState()
   - window.onpopstate 监听地址变化

4. 异同
   - hash带有“#”，且只能修改“#”后的部分，只可向satateObject中添加短字符
   - history可以修改任意同源部分，可向satateObject中添加任意类型数据

5. 注意
   - history模式则会将URL修改得就和正常请求后端的URL一样,如后端没有配置对应/user/id的路由处理，则会返回404错误，一般这个时候要配置通配符的redirector
