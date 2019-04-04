---
layout: post
title: Android 持续集成 Jenkins
category: Android
tags: Android Jenkins
keywords: Android Jenkins
---


## 持续集成 Jenkins 环境安装

1.CentOS 7
2.安装JDK
```java
#添加Yum源
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

#导入密钥
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

#安装
sudo yum install -y jenkins

#开启防火墙
systemctl start firewalld
sudo firewall-cmd --reload

#开放端口
sudo firewall-cmd --add-port=8080/tcp --permanent
sudo firewall-cmd --reload

```
### 配置Java可选路径

因为Jenkins默认的java可选路径不包含我们部署的jdk路径，所以这里要配置一下，不然Jenkins服务会启动失败
```java
#修改jenkins启动脚本

如何查找JDK的路径
1、先找到java执行文件路径
whereis java
输出：java: /opt/install/jdk1.8.0_151/bin/java

ls -lrt /opt/install/jdk1.8.0_151/bin/java

输出：-rwxr-xr-x 1 10 143 7734 9月   6 2017 /opt/install/jdk1.8.0_151/bin/java

sudo systemctl start jenkins

sudo vi /etc/init.d/jenkins

#修改candidates增加java可选路径：/opt/install/jdk1.8.0_151/bin/java
candidates="
/etc/alternatives/java
/usr/lib/jvm/java-1.8.0/bin/java
/usr/lib/jvm/jre-1.8.0/bin/java
/usr/lib/jvm/java-1.7.0/bin/java
/usr/lib/jvm/jre-1.7.0/bin/java
/usr/bin/java
/opt/install/jdk1.8.0_151/bin/java
"



```



