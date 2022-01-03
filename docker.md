> 本教程已经长时间没更新 请不要参考使用
> 推荐使用GitHub Action部署方式部署

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

### 这里给出dockerfile 有兴趣的同学可以自己折腾 就不写详细教程了
```
FROM ubuntu
COPY chromedriver /bin/
## 这里all.zip是代码压缩包 其中包括 https://github.com/billionray/ZZULI-healthreport 全部python文件以及chrome的deb包 放入deb包后请自行修改下面地址
COPY all.zip /root/ 
## 这里是打卡配置项文件
COPY data.json /root/ 

RUN  sed -i s@/archive.ubuntu.com/@/mirrors.163.com/@g /etc/apt/sources.list

ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive

RUN apt update 
RUN apt install -y tzdata zip python3 python3-pip
RUN ln -fs /usr/share/zoneinfo/${TZ} /etc/localtime 
RUN echo ${TZ} > /etc/timezone 
RUN dpkg-reconfigure --frontend noninteractive tzdata  
RUN unzip /root/all.zip  -d /root/ 
RUN dpkg -i /root/chromev88.deb ;exit 0 
RUN apt --fix-broken install -y
RUN rm -rf /var/lib/apt/lists/*
	
RUN pip3 install -r /root/requirements.txt -i https://pypi.douban.com/simple

CMD python3 /root/run.py
```
### 有兴趣的同学可以自行联系开发者取得帮助

更多有关docker的问题请移步 [Docker —— 从入门到实践](https://yeasy.gitbook.io/docker_practice/)

