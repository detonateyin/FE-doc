# JS之Object.defineProperty

1. Object.defineProperty(obj,key,{descriptor})这个方法用来定义对象属性的 **值** 和 **描述** ,descriptor配置如下
   
    - configurable 是否有权限配置描述，总开关，关闭后无法再打开，即无法再重新配置描述，同时此属性不可被删除，默认值为false
    - writable 是否有权限重写属性值，修改属性值的开关，关闭后无法重写值，默认值为false
    - enumerable 此属性是否可枚举，关闭后无法通过Object.keys()或for...in...枚举出属性，默认值为false
    - value 属性值
    - set() 与writable和value互斥，一旦目标对象访问该属性，就会调用这个方法，并返回结果。默认为 undefined。
    - get() 与writable和value互斥， 一旦目标对象设置该属性，就会调用这个方法。默认为 undefined。

2. 与 = 的区别
   
    = 是直接赋值，同时以上三个属性都为true

3. Object.getOwnPropertyDescriptor(obj,key) 获取属性的描述信息

4. get和set的运用

    - MVVM双向绑定
    - 优化对象获取和修改属性的方式，如

          Object.defineProperty(dom, 'translateX', {
            set: function(value) {
                    var transformText = 'translateX(' + value + 'px)';
                    dom.style.webkitTransform = transformText;
                    dom.style.transform = transformText;
            }
            //这样再后面调用的时候, 十分简单
            dom.translateX = 10;
            dom.translateX = -10;
            //甚至可以拓展设置如scale, originX, translateZ,等各个属性，达到下面的效果
            dom.scale = 1.5;  //放大1.5倍
            dom.originX = 5;  //设置中心点X
            }

    - 增加属性获取和修改时的信息
    - 常量
    - 等等

参考链接：

[不会Object.defineProperty你就out了](http://imweb.io/topic/56d40adc0848801a4ba198ce)

