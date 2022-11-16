From nginx:1.15.9-alpine

MAINTAINER YoungWilliam <youngwilliam.zheng@gmail.com>


WORKDIR /tmp
RUN echo 'https://mirrors.aliyun.com/alpine/v3.6/main/' > /etc/apk/repositories \
    && echo 'https://mirrors.aliyun.com/alpine/v3.6/community/' >> /etc/apk/repositories \
    && apk add git
RUN git clone https://github.com/FISCO-BCOS/fisco-bcos-browser.git && \
    cd fisco-bcos-browser && \
    mkdir -p /data/app/web/ && \
    mv web/fisco-bcos-browser-front/* /data/app/web/
