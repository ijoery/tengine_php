### Tengine + PHP for Docker

---
* 更新日志
  * 2020-4-29 添加composer支持。
  * 2020-9-13 解决了tp中PATHINFO路由重写问题 访问示例：`http://localhost/api/$1`

* 如果你不想自己去安装环境，你可以从`DockerHub`拉取镜像，或者
```
$ docker pull ijoery/tpwork:latest
```

* 安装环境
  * Tengine `version 2.3.2`
  * PHP `version 7.4.3`
* 依赖环境
  * Docker，[下载](https://docker.com)
  * Docker-compose，可通过`pip`命令进行安装。
* 下拉代码，`git clone https://github.com/ijoery/tengine_php.git`。
* 修改配置

```
version: '3'
services: 
    # 名称可自行修改
    php7.4.3-tengine2.3.2:
        build: 
            dockerfile: Dockerfile
            context: .
        ports: 
            - "80:80"
            - "443:443"
        volumes: 
            # 跟路径源码挂载目录
            - "./src:/etc/nginx/project/"
```

* 打包

```
$ cd 工作目录文件夹
# 与 docker-compose.yml 文件同级文件夹

# -d 参数为在后台运行
$ sudo docker-compose up --build -d
```

* 测试[http://localhost](http://localhost)

---

build by ijoery
