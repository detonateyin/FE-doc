# JS之难题集锦

1. add(5)(2, 3)(10) //输出20


      function add () {
          var args = Array.prototype.slice.call(arguments);

          var fn = function () {
              var arg_fn = Array.prototype.slice.call(arguments);
              return add.apply(null, args.concat(arg_fn));
          }

          fn.valueOf = function () {
              return args.reduce(function(a, b) {
                  return a + b;
              })
          }

          return fn;
        }
        add(4)(2, 3)(10) ;

    解析：

    通过递归和闭包的技巧，将args保存起来传递，在最后再通过的valueOf函数的复写，将结果返回