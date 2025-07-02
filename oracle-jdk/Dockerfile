# 使用 Alpine Linux 最新版作为基础镜像
FROM alpine:latest

# 安装依赖工具
RUN apk add --no-cache --update \
    bash \
    curl \
    tar

# 安装 Git
RUN apk add --no-cache git

# 安装 Oracle JDK 8
ENV JAVA_VERSION=8u241 \
    JAVA_BUILD=08 \
    JAVA_HASH=1f5b5a87ca1f74154c96462b4bd67e0a \
    JAVA_HOME=/usr/lib/jvm/java-8-oracle

# 下载并安装 Oracle JDK 8（使用官方二进制包）
RUN curl -jkSLH "Cookie: oraclelicense=accept-securebackup-cookie" \
    "https://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}-b${JAVA_BUILD}/${JAVA_HASH}/jdk-${JAVA_VERSION}-linux-x64.tar.gz" \
    | tar -xzf - -C /tmp && \
    mkdir -p /usr/lib/jvm && \
    mv /tmp/jdk1.8.0_241 "$JAVA_HOME" && \
    apk add --no-cache --virtual .java-runtime \
        libstdc++ \
        ca-certificates && \
    update-ca-certificates

# 配置 Java 环境变量
ENV PATH="${JAVA_HOME}/bin:${PATH}"

# 安装 Maven
ENV MAVEN_VERSION=3.9.6
RUN curl -jkSL https://dlcdn.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
    | tar -xzf - -C /usr/share && \
    mv /usr/share/apache-maven-${MAVEN_VERSION} /usr/share/maven && \
    ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

# 设置 Maven 环境变量
ENV MAVEN_HOME=/usr/share/maven

# 验证安装
RUN java -version && \
    mvn --version && \
    git --version

# 清理临时文件（Alpine 的 apk 缓存已通过 --no-cache 自动清理）
