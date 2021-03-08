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
## 基础信息
name | value
-|-
|USERNAME |你的学号
|PASSWORD |你的i轻工大密码，默认为zzuli+身份证后六位
|MOBILE |你的手机号
|HOMEMOBILE |家庭电话
|REPORTTYPE |home | morn |dorm  分别对应居家打卡、晨检打、归寝打卡 |
## 在校打卡
name | value
-|-
|REGION: | 校区 例：东风校区、科学校区、禹州实习训练基地、校外走读|
|AREA: |例：宿舍区 一区、二区、秋实区、丰华区 |
|BUILD: |例：楼号 5号楼、1号楼 |
|DORM: | 宿舍号（仅数字）|
|SCHOOLGPS: | 学校GPS地址，详细一点，例如：河南省郑州市金水区郑州轻工业大学第二学生园区|
|SCHOOLLAT: | 纬度 小数点后五位 输入时无引号 |
|SCHOOLLON: | 精度 小数点后五位 输入时无引号 |
## 居家打卡信息
name | value
-|-
|GPS |GPS定位的地址，例如：XX省XX市XX区XX街道XX小区|
|LAT |小数点后五位 纬度 输入时无引号|
|LON |小数点后五位 经度 输入时无引号|


> 经纬度查询： https://lbs.amap.com/console/show/picker 
>
> 部分手机内置指南针也可查询经纬度

## 可选：邮箱提醒

| name       | value                 |
| ---------- | --------------------- |
| MAILFLAG   | 是否需要右键提醒，输入1为需要，0为不需要|
| MYUSER     | 收件人地址            |
| MYSENDER   | 发件人地址            |
| SMTPDOMAIN | 发件人SMTP地址（SSL） |
| SMTPAUTH   | 发件人SMTP授权码      |




未完待续....