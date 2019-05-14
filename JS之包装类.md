# JS之包装类

JS只有三种包装类：
**Number**、**Boolean**、**String**

当基础类型调用方法和属性的时候，其包装类会调用构造方法生成一个对象，然后调用这个对象的方法，之后会销毁这个对象，基础类型还是基础类型

    var a = 11
    => undefined
    a.toString()
    => "11"
    typeof a
    => "number"
    Object.prototype.toString.call(a)
    => "[object Number]"

其内部实现大概是

    var a = new Number(11)
    a.toString()
    a = 11