# Docker实验报告

## Docker概念
Docker 是一种用来快速部署服务的容器技术。Docker提供简单易用的容器使用接口。它是目前最流行的 Linux 容器解决方案。Docker 将应用程序与该程序的依赖，打包在一个文件里面。运行这个文件，就会生成一个虚拟容器。程序在这个虚拟容器里运行，就好像在真实的物理机上运行一样。使用Docker,使得部署应用时不用担心环境问题。更快速的交付和部署，高效的部署和扩容，更高的资源利用率，更简单的管理。

## 使用Docker进行web应用容器化:
Docker 的配置主要依赖 Dockerfile 这一文本文件进行，文件中包含了容器构建过程中的指令。

    FROM registry.cn-shenzhen.aliyuncs.com/nodedev/nodejs:10.12.0-alpine

    ADD . /app/
    WORKDIR /app

    RUN npm install
    RUN npm rebuild node-sass --force

    ENV HOST 0.0.0.0

    ENV PORT 8000

    EXPOSE 8000
    CMD ["npm","run","dev"]

1. 该段配置使用一个 node 的中间容器，指定了工作目录为/app。
2. 其中RUN命令可以使Docker 直接在命令行中执行一条指令。
3. 命令表明容器提供的服务端口，当容器启动且未指定端口映射时会自动对指定的端口进行随机端口映射。
4. 命令是容器的启动命令，使用一个如['exec', 'param1', 'param2']的数组格式指定容器启动时的默认命令。

## 使用Dockerfile进行Mysql容器化

    FROM mysql:5.7

    ENV MYSQL_ROOT_PASSWORD = root

    RUN mysql -h127.0.0.1 -P3306 -uroot -proot

    RUN create database testdb;

    EXPOSE 3306


