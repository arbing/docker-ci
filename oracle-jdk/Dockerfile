# 使用CentOS最新官方镜像
FROM quay.io/centos/centos:stream9

# 安装Oracle JDK 8
## 设置下载链接和校验所需的Cookie
RUN JDK_URL="https://wp-img-dev-1253430620.cos.ap-beijing.myqcloud.com/oracle-jdk/jdk-8u441-linux-x64.rpm" && \
    curl -fL -b "oraclelicense=a" $JDK_URL -o /tmp/jdk.rpm && \
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
