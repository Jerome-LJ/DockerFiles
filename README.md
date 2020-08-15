# DockerFiles
常用的 Dockerfile 文件汇总

---

# TOC
- Nginx - nginx-1.18.0 Dockerfile
```
$ cd ./DockerFiles/nginx/
$ docker build -t nginx:v1.0 .
```
- Tomcat - apache-tomcat-9.0.37 Dockerfile
```
$ cd ./DockerFiles/tomcat/
$ docker build -t tomcat:v1.0 .
```
- ELKB+Cerebro - ELKB-7.8.1 docker-compose
```
#ELK
$ cd ./DockerFiles/Docker-Compose_YAML/ELKB-Compose/
$ docker-compose up --build -d
#Fliebeat
$ cd ./DockerFiles/Docker-Compose_YAML/ELKB-Compose/Fliebeat/
$ docker-compose up -d
```
- LNMP+Redis - LNMP/DNMP docker-compose
```
$ cd ./DockerFiles/Docker_Compose_YAML/LNMP-Compose/
$ docker-compose up --build -d
```
- Flask+Redis -  Flask+Redis Web docker-compose
```
$ cd ./DockerFiles/Docker_Compose_YAML/Flask-Web-Compose/
$ docker-compose up --build -d
```
---

# Docker 常用命令
```bash
# 构建 Nignx 镜像
docker build -t nginx:v1.0 .
# 查看所有镜像
docker images
# 运行 Nginx 容器
docker run --name nginx -p 80:80 -d nginx:v1.0

# 删除所有容器
docker rm -f $(docker ps -aq)  
# 删除所有镜像
docker rmi $(docker images -q)
```

---

# 温馨提示
此 DockerFiles 下所有环境都是通过 Centos:7.6.1810 构建编写。均采用官方软件包，如果构建镜像时下载软件包较慢，建议先下载好软件包到对应目录，并修改如下 Dockerfile (以Nginx为例)：
```bash
# 修改之前
RUN yum install -y gcc make pcre-devel zlib-devel zlib tar              \
    && yum clean all    \
    && curl -SL http://nginx.org/download/nginx-1.18.0.tar.gz           \
    | tar -xzC /opt    \
    && cd /opt/nginx-1.18.0         \
    && ./configure --prefix=/usr/local/nginx && make && make install    \
    && rm -rf /opt/nginx-1.18.0*    \
    && echo '<h1>Hello, Docker!</h1>' > /usr/local/nginx/html/index.html

# 修改之后
ADD nginx-1.18.0.tar.gz .

RUN yum install -y gcc make pcre-devel zlib-devel zlib tar              \
    && yum clean all    \
    && cd /opt/nginx-1.18.0         \
    && ./configure --prefix=/usr/local/nginx && make && make install    \
    && rm -rf /opt/nginx-1.18.0*    \
    && echo '<h1>Hello, Docker!</h1>' > /usr/local/nginx/html/index.html
```
