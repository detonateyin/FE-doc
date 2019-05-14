# Nunjucks之简介精要

## Nunjucks是什么

Nunjucks是Mozilia开发的模板引擎，主要用于node环境下运行

## Nunjucks的运行原理

本质就是

    function render(view, model) {
        // TODO:...
    }

## Nunjucks的特性

1. 模板替换（已经转义，防止XSS）
    
        <h1>Hello {{ name }}</h1>

        var s = env.render('hello.html', { name: '小明' });
        console.log(s);

        //  <h1>Hello 小明</h1>

2. 循环

        <body>
            <h3>Fruits List</h3>
            {% for f in fruits %}
            <p>{{ f }}</p>
            {% endfor %}
        </body>

        var s = env.render('hello.html', {fruits:['苹果','梨']});
        console.log(s);

        // <h3>Fruits List</h3>
                <p>苹果</p>
                <p>梨</p>

3. 继承/嵌套

    - base.html 定义块名称
    
            <html>
                <body>
                    {% block header %} <h3>Unnamed</h3> {% endblock %}
                    {% block body %} <div>No body</div> {% endblock %}
                    {% block footer %} <div>copyright</div> {% endblock %}
                </body>
            </html>

    - hello.html 继承父模板，并可重载模块

            {% extends 'base.html' %}
            {% block header %}<h1>{{ header }}</h1>{% endblock %}
            {% block body %}
            <div>
                {% for f in fruits %}
                <p>{{f}}</p>
                {% endfor %}
            </div>
            {% endblock %}


            var s = env.render('hello.html', {header:'HHHHHH',fruits:['苹果','梨']});
            console.log(s);

        输出后

            <html>
                <body>
                    <h1>HHHHHH</h1>
                    <div>
                        <p>苹果</p>
                        <p>梨</p>
                    </div>
                    <div>copyright</div>
                </body>
            </html>

## Nunjucks的性能

- 快速的：因为就是拼接字符串的纯CPU操作
- 主要是同步IO：但提供了缓存，只读取一次文件模板，之后就存在内存中，同时也提供了异步IO的写法


## 附录

参考链接：

1. [Nunjucks-廖雪峰](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/0014713964925087c29166d8c344a949364e40e2f28dc09000)