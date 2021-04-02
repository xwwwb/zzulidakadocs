# Linux服务器原生环境部署

> 本文基于Ubuntu 20.04 建议有Linux基础的同学阅读

## Chrome浏览器安装

打开Google Chrome官网

[点我进入](https://www.google.cn/chrome/)

翻到最底部，选择其他平台

下载Linux对应的安装包

这里下载的是deb包

通过SCP或者FTP的方式上传到Linux服务器用户主目录下

运行

```shell
sudo dpkg -i google-xxx.deb
```

中途可能会出现依赖包错误

接着执行

```shell
sudo apt --fix-broken install
```

至此Chrome安装结束

记下在安装Chrome时显示的Chrome版本号

### Chromedriver安装

[点我下载Chromedriver](https://npm.taobao.org/mirrors/chromedriver) 

选择对应Chrome版本的文件夹

下载`chromedriver_linux64.zip`

```shell
wget https://npm.taobao.org/mirrors/chromedriver/版本号/chromedriver_linux64.zip
```

解压并丢入path中

```
unzip chromedriver_linux64.zip && cp chromedriver /bin
```

输入`chromedriver`命令检查安装结果

若出现：`ChromeDriver was started successfully`

标明安装成功

## Python环境配置

Ubuntu仓库中提供有编译完成的Python安装包

可以直接通过apt下载安装

```shell
sudo apt install python3 python3-pip -y && pip3 install selenium requests
```

上述命令安装Python3以及打卡脚本所需依赖

## 打卡部署

上传仓库中的所有文件

[修改data.json文件](https://daka.xwwwb.com/#/local?id=%e5%a1%ab%e5%86%99%e9%85%8d%e7%bd%ae%e6%96%87%e4%bb%b6)

运行脚本

```shell
python3 run.py
```

若输出mission success

说明打卡成功

## 将运行脚本添加进crontab

执行

```
crontab -e
```

选择合适的编辑器

输入

```
30 * * * *  python3 run.py的绝对路径
30 8 * * *  python3 run.py的绝对路径
```

退出保存

这会在每天的8点和8点30分执行打卡任务

更多crontab的使用方法请自行百度
