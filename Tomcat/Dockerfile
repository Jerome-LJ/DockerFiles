FROM alpine:latest
LABEL Jerome="jeroome@163.com"

#配置Tomcat版本
ENV TOMCAT_VERSION=9.0.37

#修改源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

#安装Tomcat
RUN apk add --no-cache --virtual=build-dependencies wget tzdata openjdk8-jre-base \
    && export JAVA_HOME=$PATH:/usr/lib/jvm/default-jvm \
    && export PATH=${PATH}:${JAVA_HOME}/bin \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && wget https://mirrors.bfsu.edu.cn/apache/tomcat/tomcat-9/v${TOMCAT_VERSION}/bin/apache-tomcat-${TOMCAT_VERSION}.tar.gz \
    && tar zxf apache-tomcat-${TOMCAT_VERSION}.tar.gz \
    && mv apache-tomcat-${TOMCAT_VERSION} /usr/local/tomcat \
    && rm -rf apache-tomcat-${TOMCAT_VERSION}.tar.gz \
    && apk del tzdata wget

EXPOSE 8080

#设置工作目录
WORKDIR /usr/local/tomcat

#启动Tomcat
CMD ["./bin/catalina.sh", "run"]
