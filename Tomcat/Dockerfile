FROM centos:7.6.1810
LABEL Jerome="jeroome@163.com"

# 需要提前下载 jdk1.8
RUN mkdir /usr/java/
ADD jdk-8u181-linux-x64.tar.gz /usr/java/
ENV JAVA_HOME /usr/java/jdk1.8.0_181

RUN curl -SL 'https://mirrors.bfsu.edu.cn/apache/tomcat/tomcat-9/v9.0.37/bin/apache-tomcat-9.0.37.tar.gz'    \
    | tar -xzC /opt    \
    && ln -s /opt/apache-tomcat-9.0.37 /opt/tomcat

WORKDIR /opt/tomcat

EXPOSE 8080

CMD ["./bin/catalina.sh", "run"]
