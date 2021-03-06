# Fork仓库

访问本项目GitHub仓库：[点我进入](https://github.com/billionray/ZZULI-healthreport]

点击右上角按钮注册并登录Github

点击Fork按钮，将本仓库复刻到自己账号下

# 编辑secrets
个人信息传入方式为secrets传入

点击Fork后的仓库

进入settings-->secrets

点击右上角的 New repository secret按钮

依次填入：

name | value
-|-
username|你的学号
password|你的i轻工大密码，默认为zzuli+身份证后六位
moblie|你的手机号
homemobile|家庭电话
gpslocation|GPS定位的地址，例如：XX省XX市XX区XX街道XX小区
lat|小数点后五位 #纬度
lon|小数点后五位 #经度
reporttype|home \| morn \|dorm  分别对应居家打卡、晨检打、归寝打卡
|

> 经纬度查询： https://lbs.amap.com/console/show/picker 
>
> 部分手机内置指南针也可查询经纬度

可选：邮箱提醒

| name       | value                 |
| ---------- | --------------------- |
| my_user    | 收件人地址            |
| my_sender  | 发件人地址            |
| SMTPdomain | 发件人SMTP地址（SSL） |
| SMTPauth   | 发件人SMTP授权码      |
| moblie   | 手机 |



未完待续....