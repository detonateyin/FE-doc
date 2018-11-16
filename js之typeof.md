# JS之typeof

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