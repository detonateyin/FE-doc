# JS 部分问题
## 一、基础部分

### 1.MVC和MVVM的区别


    将MVC的中厚重复杂的C层抽开变为viewModle，C层弱化到只去完成数据绑定的工作即可，所有的业务逻辑放到了viewModle来完成，即为MVVM

### 2.如何识别一个数组是数组

不靠谱：
- tpyeof

靠谱：
- constructor === Array
- Object.prototype.toString.apply([]) === '[objcet Array]'
- [] instanceof Array
- 最靠谱 Array.isArray([]) 

### 3.undefined 和 null

- undefined表示"缺少值"，就是此处应该有一个值，但是还没有定义
- null表示"没有对象"，即该处不应该有值

