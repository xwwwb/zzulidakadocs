# 使用Docker部署到Linux服务器

使用docker可以快速启动打卡环境

若想手动搭建环境请移步 [使用Docker部署到Linux服务器](https://daka.xwwwb.com/#/docker)

本项目GitHub地址：[点我进入](https://github.com/xwwwb/ZZULI-healthreport-docker)

# 如何使用

### docker安装

```shell
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

更多有关docker安装的问题请移步 [这里](https://yeasy.gitbook.io/docker_practice/install/ubuntu)

### 环境配置

```shell
git clone https://github.com/xwwwb/ZZULI-healthreport-docker.git # 下载仓库
cd ZZULI-healthreport-docker
vi run.py # 修改配置文件
docker build -t zzulidaka:1.0 . # 使用dockerfile创建镜像
docker run --rm zzulidaka:1.0 # 运行一次，可以将此命令添加进crontab
```

### dockerfile讲解

```
FROM ubuntu # 构建自Ubuntu
COPY chromev88.deb /root # 这里使用了Chrome 88
COPY chromedriver /bin # 这里是Chrome 88对应的chromedriver
COPY run.py /root # 打卡脚本
COPY Services.py /root # 打卡脚本
COPY sources.list /etc/apt/ # 修改apt软件源为网易镜像站加速apt访问，国外服务器可注释这一行
RUN cd /root && dpkg -i chromev88.deb ; exit 0 # 安装Chrome 这里可能会报错为了保证build继续加入 exit 0
RUN apt update # 更新软件列表
RUN DEBIAN_FRONTEND=noninteractive apt --fix-broken install -y # 修复Chrome依赖完成Chrome安装
RUN apt install python3 python3-pip -y && pip3 install selenium requests # 安装Python3 以及所需依赖
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime # 修改时区为上海
RUN dpkg-reconfigure -f noninteractive tzdata # 修改时区
CMD python3 /root/run.py # 运行镜像时执行打卡脚本
```

更多有关docker的问题请移步 [Docker —— 从入门到实践](https://yeasy.gitbook.io/docker_practice/)

