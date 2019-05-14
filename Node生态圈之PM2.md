# Node生态圈之PM2

本文基本上是直接转载了[《PM2简易使用手册》](https://juejin.im/post/5be406705188256dbb5176f9),再此仅做存档以便查询

### 一、PM2简介

pm2（process manager）是一个进程管理工具，维护一个进程列表，可以用它来管理你的node进程，负责所有正在运行的进程，并查看node进程的状态，也支持性能监控，负载均衡等功能。

### 二、PM2的主要特性
- 内建负载均衡（使用 Node cluster 集群模块）
- 后台运行
- 0 秒停机重载，我理解大概意思是维护升级的时候不需要停机.
- 具有 Ubuntu 和 CentOS 的启动脚本
- 停止不稳定的进程（避免无限循环）
- 控制台检测
- 提供 HTTP API
- 远程控制和实时的接口 API ( Nodejs 模块,允许和 PM2 进程管理器交互 )

### 三、命令

#### 安装

    // 全局安装pm2，依赖node和npm
    npm install -g pm2

#### 启动

    pm2 start

    // start命令启动对应的node server文件
    pm2 start ./build/server.js

#### 查看详细状态信息

    pm2 show (appname|id)

#### 查看所有启动的进程列表

    pm2 list

#### 监控每个 node 进程的 cpu 和内存使用情况

    pm2 monit

#### 显示所有进程的日志信息

    pm2 logs

#### 监控运行这些进程的机器的状态

    pm2 web

#### 停止 指定/所有 进程

    pm2 stop (id|all)

#### 重启 指定/所有 进程
    
    pm2 restart (id|all)  

#### 杀死 指定/所有 进程

    pm2 delete (id|all)

#### 负载均衡

    pm2 start server.js -i (number|max)

    # 开启三个进程运行项目
    pm2 start app.js -i 3
    # 根据机器CPU核数，开启对应数目的进程运行项目
    pm2 start app.js -i max

    配置文件里对应的："instance": (number|max)
    // pm2.config.js
    "instances": 2,  // 启动两个实例


### 四、配置文件


    module.exports = {
        apps: [
            {
                name: 'kaifazhe', // 应用名称
                script: './build/server.js', // 启动文件地址
                cwd: './', // 当前工作路径
                watch: [
                    // 监控变化的目录，一旦变化，自动重启
                    'src',
                    'build',
                ],
                ignore_watch: [
                    // 忽视这些目录的变化
                    'node_modules',
                    'logs',
                    'public',
                ],
                node_args: '--harmony', // node的启动模式
                env: {
                    NODE_ENV: 'development', // 设置运行环境，此时process.env.NODE_ENV的值就是development
                    ORIGIN_ADDR: 'http://www.yoduao.com'
                },
                env_production: {
                    NODE_ENV: 'production',
                },
                out_file: './logs/out.log', // 普通日志路径
                error_file: './logs/err.log', // 错误日志路径
                merge_logs: true,
                log_date_format: 'YYYY-MM-DD HH:mm Z',
                },
            ],
        };

> 对于上面的 env，我们可以在内部添加很多个参数变量，这样我们所使用的 process.env.XXX 就会对应发生变化,例如上面，我们 process.env.ORIGIN_ADDR 的值就是http://www.youdao.com


### 五、相关生态

配合pm2-web实现监控可视化

## 附录
参考链接：
1. [PM2使用手册](https://juejin.im/post/5be406705188256dbb5176f9)