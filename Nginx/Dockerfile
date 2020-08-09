FROM centos:7.6.1810 as build
LABEL Jerome="jeroome@163.com"

EXPOSE 80

WORKDIR /opt

RUN yum install -y gcc make pcre-devel zlib-devel zlib tar              \
    && yum clean all    \
    && curl -SL 'http://nginx.org/download/nginx-1.18.0.tar.gz'         \
    | tar -xzC /opt    \
    && cd /opt/nginx-1.18.0         \
    && ./configure --prefix=/usr/local/nginx && make && make install    \
    && rm -rf /opt/nginx-1.18.0*    \
    && echo '<h1>Hello, Docker!</h1>' > /usr/local/nginx/html/index.html


FROM centos:7.6.1810
LABEL Jerome="jeroome@163.com"

EXPOSE 80

VOLUME ["/usr/local/nginx/html"]

COPY --from=build /usr/local/nginx /usr/local/nginx

CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
