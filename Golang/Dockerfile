FROM alpine:latest
LABEL Jerome="jeroome@163.com"

#修改源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

RUN apk --no-cache add go git ca-certificates tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata \
    && chmod -R 777 /go

ENV GOROOT /usr/lib/go
ENV GOPATH /usr/lib/go/bin
ENV PATH /usr/bin/go:$PATH
