
# JS之arguments

1. arguments是所有函数（除了箭头函数，箭头函数不暴露此对象）内部的局部变量，是一个所有实参的类数组
    - 类数组，只有length属性，而没有array的其他方法
    - 对arguments[n]赋值，会改变实际实参的值

          function func2(a){
            arguments[0] = 0
            console.log(arguments)
          }
          func2(1) // 0

    - 可通过Array.prototype.XXXX.call(arguments)来实现其他array的属性和方法
    - arguments.callee引用函数自身
    - 函数名.caller可以返回此函数的调用者

          function callerTest(){

            if(callerTest.caller){
              var caller = callerTest.caller.toString();
              console.log(caller);
            }else{
              console.log("no caller")
            }
          }

          function handler(){
            callerTest();
          }

          function handlerToHandler(){
            handler();
          }

          callerTest();        //no caller
          handler();           //返回调用者handler函数
          handlerToHandler();  //返回调用者handler函数

    - 针对arguments的类型判断如下

          
          console.log(arguments) // Arguments[...]
          console.log(typeof arguments) // 'object'
          console.log(arguments instanceof Array) // false
          console.log(arguments instanceof Object) // true
          console.log(Object.prototype.toString.call(arguments)) // '[object Arguments]'

2.  arguments的应用
    - 方法重载

      

      

参考文章：

[Arguments 对象深入了解](https://juejin.im/entry/57ec8215bf22ec00643d7a02)