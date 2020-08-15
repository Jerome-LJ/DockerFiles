FROM alpine:latest as build
LABEL Jerome="jeroome@163.com"

#配置Nginx版本
ENV PCRE_VERSION=8.44
ENV NGINX_VERSION=1.18.0

EXPOSE 80

#修改源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

#安装需要编译nginx扩展
#安装正则表达式pcre模块，nginx正则匹配URL
RUN apk add --no-cache --virtual=build-dependencies wget gcc g++ make tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && cd /opt \
    && wget "https://ftp.pcre.org/pub/pcre/pcre-${PCRE_VERSION}.tar.gz" \
    && tar xvf pcre-${PCRE_VERSION}.tar.gz \
    && wget "http://nginx.org/download/nginx-${NGINX_VERSION}.tar.gz" \
    && tar xvf nginx-${NGINX_VERSION}.tar.gz \
    #编译nginx
    && cd /opt/nginx-${NGINX_VERSION} \
    && ./configure --prefix=/usr/local/nginx --with-pcre=/opt/pcre-${PCRE_VERSION} --without-http_gzip_module \
    && make && make install \
    && rm -rf /opt/* \
    && apk del wget gcc g++ make tzdata \
    && echo '<h1>Hello, Docker!</h1>' > /usr/local/nginx/html/index.html


FROM alpine:latest
LABEL Jerome="jeroome@163.com"

EXPOSE 80

#设置工作目录
WORKDIR /usr/local/nginx

COPY --from=build /usr/local/nginx /usr/local/nginx

#启动Nginx
CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
