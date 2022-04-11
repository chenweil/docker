## 基于docker搭建laravel项目
公司PHP项目是Laravel框架写的，目前环境需要通过docker来部署一下。网上学习了一下相关知识。整理后做一个笔记。
主要参考项目：
《docker完美搭建laravel运行环境》[<sup>参考1</sup>](#refer-anchor-1)
项目时间比较久，其中作者提供的镜像与我项目版本不同。我更新了其中PHP版本为php-fpm7.4。

## 配置
* 项目导入 www/source
* 配置nginx/conf.d
* 配置MySQL&redis
* 配置定时任务cron/laravel
* 配置supervisor管理进程 xx.conf
## 启动方法
配置完成启动
`docker-compose up -d`
## 目录
```ini
├── README-laravel.md
├── README.md
├── docker-compose.yml
├── exec.sh
├── my.cnf
├── mysql
│   ├── auto.cnf
│   └── ...
├── nginx
│   ├── conf.d
│   │   ├── proxy.conf  # 前后端代理配置
│   │   ├── server.conf # 后端服务配置
│   │   └── web.conf    # 前端服务配置
│   ├── demo_php_conf.d.conf # 示例文件
│   └── nginx.conf
├── php-fpm
│   ├── cron            # 定时任务配置
│   │   └── laravel
│   ├── php.ini-production
│   └── supervisor      # supervisor配置
│       ├── program.conf
│       └── supervisord.conf
├── redis
│   └── redis.conf
└── www
    └── source
        jiankongweb # 前端目录
        │   ├── favicon.ico
        │   ├── index.html
        │   └── static
        │   │   ├── ...
        ├── line_monitor #后端目录
        │   ├── README.md
        │   ├── app
        │   ├── ...    
```

## 快捷指令
exec.sh方便进入各容器。
`exec.sh 容器name/ID`
进入nginx：
 `exec.sh nginx` = `docker exec -it nginx bash`

## composer
进入PHP容器可以运行composer。

---
## 参考：

<div id="refer-anchor-1"></div>

- [1] [精灵GG-docker完美搭建laravel运行环境](https://www.jianshu.com/p/6c779d7f6f29)

<div id="refer-anchor-2"></div>

- [2] [xiaoemoxiw/docker](https://github.com/xiaoemoxiw/docker)