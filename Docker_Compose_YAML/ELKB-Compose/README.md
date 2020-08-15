# 使用 Docker 部署 ELKB 环境
# 组件版本
```
Elasticsearch: 7.8.1
Logstash: 7.8.1
Kibana: 7.8.1
Filebeat: 7.8.1
```
# 目录结构
```
├── Docker-Compose_YAML
    └── ELKB-Compose
        ├── cerebro                 Cerebro 目录
        │   ├── conf                Cerebro 配置文件目录
        │   └── logs                Cerebro 日志目录
        ├── docker-compose.yml      Docker 服务配置示例文件
        ├── elasticsearch           Elasticsearch 目录
        │   ├── es-node-01          ES 01 节点目录
        |       ├── data            ES 01 节点数据目录
        |       └── logs            ES 01 节点日志目录
        ├── fliebeat                Filebeat 目录
        │   └── docker-compose.yml  Filebeat Docker 服务配置示例文件
        ├── kibana                  Kibana 目录
        │   └── data                Kibana 数据目录
        └── logstash                Logstash 目录
            ├── pipeline            Logstash pipeline 文件目录
            ├── data                Logstash 数据目录
            └── log                 Logstash 日志目录
```
# 安装步骤
```bash
$ cd ~/
$ git clone https://github.com/Jerome-LJ/DockerFiles.git

$ cd ./DockerFiles/Docker-Compose_YAML/ELKB-Compose/
$ cp .env-example .env

# 配置ELKB环境端口
$ vim .env

# 构建镜像并启动容器
$ docker-compose up --build -d
```
# 测试
使用`docker ps`查看容器启动状态，若全部正常启动。则通过访问如下链接，即可完成测试。
ES默认端口为9200
> http://127.0.0.1:9200/

Kibana默认端口为5601
> http://127.0.0.1:5601/

Cerebro默认端口为9000
> http://127.0.0.1:9000/