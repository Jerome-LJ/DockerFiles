# 使用 Docker 部署 LNMP+Redis 环境
# 组件版本
```
Nginx: 1.18.0
MySQL: 5.7
PHP: 7.4.9-fpm-alpine
Redis: 6.0.6
```
# 目录结构
```
├── Docker_Compose_YAML
    └── LNMP-Compose
        ├── docker-compose.yml      Docker 服务配置示例文件
        ├── mysql                   MySQL 目录
        │   ├── data                数据库数据目录
        │   ├── log                 数据库日志目录
        │   └── my.cnf              数据库配置文件
        ├── nginx                   Nginx 目录
        │   ├── conf.d              Nginx 配置文件目录
        │   │   └── default.conf
        │   ├── log                 Nginx 日志目录
        │   └── nginx.conf          Nginx 配置文件
        ├── php                     PHP 目录
        │   ├── conf                PHP 配置文件目录
        │   │   ├── php-fpm.conf
        │   │   └── php.ini
        │   ├── Dockerfile          PHP Dockerfile 示例文件
        │   ├── log                 PHP 日志目录
        │   └── www                 PHP 代码文件目录
        │       ├── db.php
        │       ├── index.php
        │       └── redis.php
        ├── README.md               README
        └── redis                   Redis 目录
            ├── data                Redis 数据目录
            ├── log                 Redis 日志目录
            └── redis.conf          Redis 配置文件
```
# 安装步骤
```bash
$ cd ~/
$ git clone https://github.com/Jerome-LJ/DockerFiles.git

$ cd ./DockerFiles/Docker_Compose_YAML/LNMP-Compose/
$ cp .env-example .env

# 配置数据库密码、端口等
$ vim .env

# 构建镜像并启动容器
$ docker-compose up --build -d
```
# 测试
使用`docker ps`查看容器启动状态，若全部正常启动。则通过访问如下链接，即可完成测试。
> http://127.0.0.1/
> http://127.0.0.1/index.php
> http://127.0.0.1/db.php
> http://127.0.0.1/redis.php
