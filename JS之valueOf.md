# JS之valueOf 和 toString

1. valueOf

    MDN描述，“JavaScript调用valueOf方法将对象转换为原始值。你很少需要自己调用valueOf方法；当遇到要预期的原始值的对象时，JavaScript会自动调用它。”

    一句话： 用来获取 **原始值** 的

    对象 | 返回值
    --|--
    Array | 数组本身
    Boolean | 布尔值
    Date | 毫秒值
    Function | 函数本身
    Number | 数字值
    Object | 对象本身
    String | 字符串值

2. toSrting

  MDN描述，“每个对象都有一个toString()方法，当该对象被表示为一个文本值时，或者一个对象以预期的字符串方式引用时自动调用。默认情况下，toString()方法被每个Object对象继承。如果此方法在自定义对象中未被覆盖，toString() 返回 "[object type]"，其中type是对象的类型。”

  一句话：
  
  普通对象返回 "[object type]"，基本类型会调用包装类重载的toSring()方法
  
