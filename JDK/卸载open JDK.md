先看看有没有安装
```
java -version
```
查找他们的安装位置
```
rpm -qa | grep java
```
使用 rpm -e --nodeps进行强制卸载
```
rpm -e --nodeps
```