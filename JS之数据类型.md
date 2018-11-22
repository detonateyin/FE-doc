# JS之数据类型

## 一、基本数据类型
  - Number
  - String
  - Boolean
  - Object
  - Null
  - undefinded
  - Symbol(ES5)

## 二、数据类型判断
- typeof
- toString
- instanceof
- constructor

1. ### typeof

    typeof实现原理：
    JS在底层存储变量时，会在变量的机器码的低位1-3位储存其类型信息，如下：
    - 000 对象
    - 010 浮点数
    - 100 字符串
    - 110 布尔
    - 1 整数

    特殊：
    - 全是0 Null
    - -2^30 undefined

    所以用typeof判断null时，由于其全是0，就会返回对象

    Type | Result
    --- | --
    Undefined | "undefined"
    Null | "object"
    Boolean | "boolean"
    Number | "number"
    String | "string"
    Function | "function"
    Object | "object"
    Symbol | "symbol"
    Host object | *Implementation-dependent*

2. ### Object.prototype.toString.call

   
       Object.prototype.toString.call(1)// "[object Number]"

       Object.prototype.toString.call('hi') // "[object String]"

       Object.prototype.toString.call({a:'hi'}) // "[object Object]"

       Object.prototype.toString.call([1,'a']) // "[object Array]"

       Object.prototype.toString.call(true) // "[object Boolean]"

       Object.prototype.toString.call(() => {}) // "[object Function]"

       Object.prototype.toString.call(null) // "[object Null]"

       Object.prototype.toString.call(undefined) // "[object Undefined]"

       Object.prototype.toString.call(Symbol(1)) // "[object Symbol]"

       Object.prototype.toString.call(new Date()) // "[object Date]"

       Object.prototype.toString.call(/abc/) // "[object RegExp]"

3. ### instanceof

    检查原型链

4. ### constructor



