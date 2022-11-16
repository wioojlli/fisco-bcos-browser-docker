FROM gradle:jdk8

MAINTAINER YoungWilliam <youngwilliam.zheng@gmail.com>

LABEL Version="2.0"
LABEL Name="fisco-bcos-browser 2.0"
LABEL Description="Oracle Jre 8 + gradle 5.2.1"

# python package
RUN sed -i 's/archive.ubuntu.com/mirrors.cloud.tencent.com/g' /etc/apt/sources.list \
    && sed -i 's/security.ubuntu.com/mirrors.cloud.tencent.com/g' /etc/apt/sources.list \
    && apt-get update \
    && apt-get install -y python3-pip \
    && pip3 install PyMySQL \
    && rm -f /usr/bin/gradle \
    && rm -rf /opt/gradle
WORKDIR /opt
RUN wget https://services.gradle.org/distributions/gradle-6.1-bin.zip \
    && unzip gradle-6.1-bin.zip \
    && rm -f gradle-6.1-bin.zip \
    && ln -s /opt/gradle-6.1/bin/gradle /usr/bin/gradle

RUN git clone https://github.com/FISCO-BCOS/fisco-bcos-browser.git /fisco-bcos-browser

WORKDIR /fisco-bcos-browser/server/fisco-bcos-browser
RUN gradle build
RUN cp dist/conf_template dist/conf -r

WORKDIR /fisco-bcos-browser/server/fisco-bcos-browser/dist/

RUN chmod +x ./start.sh

CMD ["sh", "start.sh"]
