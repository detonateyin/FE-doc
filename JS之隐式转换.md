# JS值隐式转换


今天阅读了 **keenjaan** 在掘金写的一篇文章[《你所忽略的js隐式转换》](https://juejin.im/post/5a7172d9f265da3e3245cbca)，此文清晰明了的解释JS发生隐式转换的原理及规律，有兴趣的同学推荐原味观看。在此仅做总结补充，以供我之后复习

1. 为什么发生隐式转换？

    因为JS是动态弱类型语言，只有当运行时才能知道变量的类型，所以在发生运算时，需要完成隐式转换才能进行，比如最常见的“+”、“==”，还有Number类型下的“*”、“/”等

2. JS的数据类型
   
   要搞清楚JS的隐式转换，需明白JS的数据类型有两种分别：
    - 原始类型
      - Number
      - Boolean
      - String
      - undefined
      - null
      - Symbol（ES6）
    - 复杂类型
      - Object

    数据类型转换都是先在这两种类型间的转换，准确点来说，如果发生此二类型转换，都是复杂类型先向基本类型转

3. 隐式转换的规律
   
    - 第一步，先完成ToPrimitive(input,PreferredType)
    - 第二部，根据PreferredType的值完成转换
      - Number签名，完成ToNumber（）
      - String签名，完成ToString（）

4. ToPrimitive(input,PreferredType)的内部运行机制

    总结一句话，Number标识先调用valueOf，后调用toString，String标识反之

    - Number标识
        1. 如果input是原始类型，直接返回
        2. 不是原始类型，则先调用对象的valueOf()函数，如果此函数返回原始类型，则返回
        3. 如果valueOf()没有返回原始类型，调用toString()函数，如果原始类型则返回
        4. 否则抛出“无法将此对象转换为原始类型”的错误

    - String标识
        1. 如果input是原始类型，直接返回
        2. 调用toString()函数，如果函数返回原始类型，则返回
        3. 不是原始类型，则调用对象的valueOf()函数，如果此函数返回原始类型，则返回
        4. 否则抛出“无法将此对象转换为原始类型”的错误

    - 没有标识符
        1. 如果input是Date类型，则用String标识符
        2. 否则，用Number

    - 匹配标识规则
        1. 限定Number的操作，比如“*”，“-”，“/”，只能是Number的标识
        2. == 操作符有下面详解

5. 关于valueOf和toString的运行机制

    - 只要是对象，都有此二方法，通过prototype链继承而来
    - 预设包装类：Number、String、Boolean、Funciton、Array、Math、Date、RegExp
      - valueOf
        - Number、String、Boolean、Date都重载了，前三项返回原始类型值，Date返回毫秒值
        - 其他都是返回本身this
      - toString
        - Number、String、Boolean、Funciton、Array、Date、RegExp重载了
        - 其他都返回“[object Type]”

6. 原始类型间的转换
   
    - toNumber

        参数 | 结果
        -|-
        Number | 无需转换
        String | ''为0，'123'为123，'12qw'为NaN
        Boolean | true为1，false为0
        undefined | NaN
        Null | 0
        Object | 先ToPrimitive，再ToNumber

    - toString

        参数 | 结果
        -|-
        Number | '数字'
        String | 无需转换
        Boolean | 'Boolean'
        undefined | 'undefined'
        Null | 'null'
        Object | 先ToPrimitive，再ToString

7. == 操作符详解
   
   此操作符比较复杂，简短总结：
   
   - **类型相同，原始类型直接比较值，对象则比较引用地址**
   - **类型不同，则最终都使用Number标识，调用ToNumber后进行比较**
   
   详细部分我就直接粘贴[《你所忽略的js隐式转换》](https://juejin.im/post/5a7172d9f265da3e3245cbca)的详解例子

   >比较运算 x==y, 其中 x 和 y 是值，返回 true 或者 false。这样的比较按如下方式进行：

        1、若 Type(x) 与 Type(y) 相同， 则

            1* 若 Type(x) 为 Undefined， 返回 true。
            2* 若 Type(x) 为 Null， 返回 true。
            3* 若 Type(x) 为 Number， 则
        
                (1)、若 x 为 NaN， 返回 false。
                (2)、若 y 为 NaN， 返回 false。
                (3)、若 x 与 y 为相等数值， 返回 true。
                (4)、若 x 为 +0 且 y 为 −0， 返回 true。
                (5)、若 x 为 −0 且 y 为 +0， 返回 true。
                (6)、返回 false。
                
            4* 若 Type(x) 为 String, 则当 x 和 y 为完全相同的字符序列（长度相等且相同字符在相同位置）时返回 true。 否则， 返回 false。
            5* 若 Type(x) 为 Boolean, 当 x 和 y 为同为 true 或者同为 false 时返回 true。 否则， 返回 false。
            6*  当 x 和 y 为引用同一对象时返回 true。否则，返回 false。
        
        2、若 x 为 null 且 y 为 undefined， 返回 true。
        3、若 x 为 undefined 且 y 为 null， 返回 true。
        4、若 Type(x) 为 Number 且 Type(y) 为 String，返回比较 x == ToNumber(y) 的结果。
        5、若 Type(x) 为 String 且 Type(y) 为 Number，返回比较 ToNumber(x) == y 的结果。
        6、若 Type(x) 为 Boolean， 返回比较 ToNumber(x) == y 的结果。
        7、若 Type(y) 为 Boolean， 返回比较 x == ToNumber(y) 的结果。
        8、若 Type(x) 为 String 或 Number，且 Type(y) 为 Object，返回比较 x == ToPrimitive(y) 的结果。
        9、若 Type(x) 为 Object 且 Type(y) 为 String 或 Number， 返回比较 ToPrimitive(x) == y 的结果。
        10、返回 false。


8. 特殊案例
    1. undefined == null // true  因为规范规定了此条
    2. NaN !== NaN // true 