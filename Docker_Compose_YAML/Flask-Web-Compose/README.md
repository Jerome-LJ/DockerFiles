# 使用 Docker 部署 Flask+Redis 环境
# 组件版本
```
Python: 3.8-alpine
Redis: 6.0.6
```
# 目录结构
```
├── Docker-Compose_YAML
    └── Flask-Web-Compose
        ├── app.py              App 应用程序
        ├── docker-compose.yml  Docker 服务配置示例文件
        └── Dockerfile          Dockerfile 示例文件
```
# 安装步骤
```bash
$ cd ~/
$ git clone https://github.com/Jerome-LJ/DockerFiles.git

$ cd ./DockerFiles/Docker-Compose_YAML/Flask-Web-Compose/
$ cp .env-example .env

# 配置App应用程序端口
$ vim .env

# 构建镜像并启动容器
$ docker-compose up --build -d
```
# 测试
使用`docker ps`查看容器启动状态，若全部正常启动。则通过访问如下链接，即可完成测试。
> http://127.0.0.1:8000/
