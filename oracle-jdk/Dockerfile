# 使用CentOS最新官方镜像
FROM centos:latest

# 安装基础工具
RUN yum update -y && \
    yum install -y curl tar gzip && \
    yum clean all

# 安装Oracle JDK 8
## 设置下载链接和校验所需的Cookie
ARG JDK_VERSION=8u401
ARG JDK_BUILD=10
ARG JDK_SHA256=df884f6e1ead9a4c5b77c2d7c1a48f5c4b47ec8f000e9b66adfc0b6d99a3f3b7
RUN JDK_URL="https://download.oracle.com/java/${JDK_VERSION:0:1}/archive/jdk-${JDK_VERSION}-linux-x64.rpm" && \
    curl -fL -b "oraclelicense=a" $JDK_URL -o /tmp/jdk.rpm && \
    echo "${JDK_SHA256} /tmp/jdk.rpm" | sha256sum -c - && \
    yum localinstall -y /tmp/jdk.rpm && \
    rm -f /tmp/jdk.rpm && \
    java -version

# 安装Git
RUN yum install -y git && \
    yum clean all

# 安装Maven
ARG MAVEN_VERSION=3.8.6
ARG MAVEN_SHA=4c105a9ffed0c193edd0e06e888ef18a6d5831d5b4947648e21b1d0b8b04e575
RUN mkdir -p /usr/share/maven && \
    curl -fL https://archive.apache.org/dist/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz -o /tmp/maven.tar.gz && \
    echo "${MAVEN_SHA}  /tmp/maven.tar.gz" | sha256sum -c - && \
    tar -xzf /tmp/maven.tar.gz -C /usr/share/maven --strip-components=1 && \
    rm -f /tmp/maven.tar.gz && \
    ln -s /usr/share/maven/bin/mvn /usr/bin/mvn && \
    mvn --version

# 设置环境变量
ENV JAVA_HOME /usr/java/latest
ENV MAVEN_HOME /usr/share/maven
ENV PATH $JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH

# 验证安装
RUN java -version && \
    git --version && \
    mvn --version
